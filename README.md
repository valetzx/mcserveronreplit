# Minecraft Server - Setup Guide
> Warning: Nix support on Replit is still under heavy development. Works best if the repl is boosted.

You've just created a personal Minecraft Server. To ensure that everyone can partake, this guide is divided into 2 parts. However, you can use this as the starting point for *ANY MINECRAFT SERVER*

If you're a beginner player, looking for a Minecraft server (no mods) to play on with just a couple of your friends, I suggest following the `Basic Server` instructions.

If you're an experienced player, looking for a Minecraft server (with mods) and a large number of users, I suggest following the `Modded Server` instructions.

---
## Basic Server
> We're working with a very reputable and well optimized server type - Paper Server.

1) Inside of `Startup.sh`, set your preferred server version and build. If you are unsure, leave that to the default `1.18.1` and `216`.

2) Click on the padlock on the far left side of your screen and edit`ngrok_region` secret and input one of the regions from the list below as the value. *Choose the closest region for better network connectivity.*

```
#List of all the regions
  us - United States (Ohio)
  eu - Europe (Frankfurt)
  ap - Asia/Pacific (Singapore)
  au - Australia (Sydney)
  sa - South America (Sao Paulo)
  jp - Japan (Tokyo)
  in - India (Mumbai)" 
```

3) Edit the `ngrok_token` secret and input your ngrok authtoken as the value. *If you don't have a ngrok authtoken, you can [visit here](https://dashboard.ngrok.com) and make an account to get your token. *

4) Run the repl and follow the instructions on the console. *This will automatically install the server files corresponding with the server version specified in Step 1 .*

5) Once the console displays `Done! For help, type "help"`, navigate to `ip.txt` and copy the whole ip and enter it inside Minecraft.

*__Optional: __*
  * Navigate to `server.properies` inside the `Server` folder to further personalise the server. 
  * Plug-ins can be added to the `Plugins` folder inside the Server folder. Paper servers support both [Bukkit](https://www.curseforge.com/minecraft/bukkit-plugins) and [Spigot](https://www.spigotmc.org/resources/authors) plug-ins as long as they correspond to the server version.

---
## Modded Server

1) Navigate to `Startup.sh` and comment out line 29 to avoid installing the default paper server.

2) Manually download and add a `server.jar` file to the `Server` directory.
>Minecraft version 1.12.2 is one of the most stable versions of Minecraft, it also has the most amount of mods. If you are looking for just mods, follow the instructions for `Forge`. However if you want both Mods and Plug-ins, follow the instructions for `Magma`.

* Forge:
  * [Visit the Forge website](https://files.minecraftforge.net/net/minecraftforge/forge/index_1.12.2.html) and download your preferred version as an Installer. *Please do some research for compatible plug-ins beforehand.*
  * Double-click and run the installation via Java on you computer. Input an extraction location, select "Install server" and finally press ok.
  * After it's finished extracting, move all the extracted files into the Server directory.

* Magma:
  * [Visit the Magma website](https://magmafoundation.org/) and download your preferred version as an Installer for version 1.16.x and Dev for version 1.12.x. Make sure the files is renamed to `server.jar` and is placed in the `Server` directory
  * Navigate to the bottom of `Startup.sh`. For version 1.16.x, uncomment line 115 otherwise skip this.

3) Add some environment variables to this repl. *Follow Steps 2 and 3 of the `Basic Server Guide`* 

4) Run the repl. 
* Forge server and Magma version 1.12.x will start up normally and install all the server files from the web automatically. Follow the instructions on the console. (Skip Step 5)

* Magma 1.16.x requries an additional parameter `--installServer` to install the server files. This is already added to `Startup.sh` on line 115, you just need to uncomment it, and comment out line 114. 


5) After running Magma 1.16.x with the installation parameter, it will extract 2 .jar files into the Server directory. You can delete the server.jar file, and `rename the Forge-[Version].jar file to server.jar`. Then navigate back to `Startup.sh` and switch back to starting up with line 114. Run the repl and the server should start.

> *If the console throws an error stating incompatible Java version, refer to FAQ 3 of this guide.*

----
## FAQ

* ### How many players can play on the server?
  * Servers running on boosted repls and proper optimizations can handle at least 100 players with stable TPS. 


* ### How do I optimize my server?
  * Having more than 1 boosted repls can affect server performance. Try to only boost this 1 repl.
  
  * It is recommended to pre-generate all the chunks using the plug-in [Fast Chunk Pre-generator](https://www.spigotmc.org/resources/fast-chunk-pregenerator.74429/) to clear most of the block lagg.
  
  * There are some plug-ins such as [Clearlagg](https://www.spigotmc.org/resources/clearlagg.68271/) that can clear entities which futher improves the server performance. 

  * Paper servers allow the server operators to limit how many mobs can spawn, decreasing the amount improves the overall TPS of the server.


* ### I got an error saying "... only supports Java *x*"
  * Different Minecraft versions have different requirements of minimum Java version. From Java Edition 1.12 (17w13a) to Java Edition 1.16.5 (1.17: 21w18a), Minecraft requires Java 8 or newer. Since Java Edition 1.17 (21w19a), Minecraft requires Java 16 or newer.

  * Navigate to `replit.nix` and follow these intructions:
    * For Minecraft 1.12.x - add the packages `pkgs.jre8` and `pkgs.jdk8` to the list. *Please don't forget to remove `pkgs.jdk16_headless`*

    * For Minecraft 1.17 - make sure `pkgs.jdk_headless` is included.

---
## Enjoy!

I hope you were successful in making your own Minecraft server, if you have any questions, please tweet @SimerLol and I will try to reply as soon as possible. Have a great day!
