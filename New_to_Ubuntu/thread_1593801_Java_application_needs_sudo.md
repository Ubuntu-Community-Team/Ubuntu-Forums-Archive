---
title: "Java application needs sudo"
date: 2010-10-11
forum: New to Ubuntu
---

### Post by risegeek on 2010-10-11
I am running a minecraft server - I have read many tutorials on how to get it running and it works perfect :) however I have not seen anyone with this problem. I need to run this with sudo or it will give errors.

```
java -Xmx640M -Xms640M -jar minecraft_server.jar nogui
2010-10-11 23:09:34 [WARNING] Failed to log to server.log
java.io.FileNotFoundException: server.log (Permission denied)
        at java.io.FileOutputStream.open(Native Method)
        at java.io.FileOutputStream.<init>(FileOutputStream.java:209)
        at java.io.FileOutputStream.<init>(FileOutputStream.java:131)
        at java.util.logging.FileHandler.open(FileHandler.java:173)
        at java.util.logging.FileHandler.rotate(FileHandler.java:552)
        at java.util.logging.FileHandler.openFiles(FileHandler.java:440)
        at java.util.logging.FileHandler.<init>(FileHandler.java:254)
        at fk.a(SourceFile:47)
        at net.minecraft.server.MinecraftServer.d(SourceFile:90)
        at net.minecraft.server.MinecraftServer.run(SourceFile:186)
        at bm.run(SourceFile:480)
2010-10-11 23:09:34 [INFO] Starting minecraft server version 0.2.1
2010-10-11 23:09:34 [INFO] Loading properties
2010-10-11 23:09:34 [INFO] Starting Minecraft server on 208.115.211.47:25565
2010-10-11 23:09:34 [WARNING] Failed to save ban list: java.io.FileNotFoundException: banned-players.txt (Permission denied)
2010-10-11 23:09:34 [WARNING] Failed to save ip ban list: java.io.FileNotFoundException: banned-ips.txt (Permission denied)
2010-10-11 23:09:34 [WARNING] Failed to save ip ban list: java.io.FileNotFoundException: ops.txt (Permission denied)
2010-10-11 23:09:34 [INFO] Preparing level "flatgrass"
2010-10-11 23:09:34 [INFO] Preparing start region
java.lang.RuntimeException: Failed to check session lock, aborting
        at dy.<init>(SourceFile:168)
        at dy.<init>(SourceFile:144)
        at ee.<init>(SourceFile:35)
        at net.minecraft.server.MinecraftServer.c(SourceFile:139)
        at net.minecraft.server.MinecraftServer.d(SourceFile:130)
        at net.minecraft.server.MinecraftServer.run(SourceFile:186)
        at bm.run(SourceFile:480)
2010-10-11 23:09:34 [SEVERE] Unexpected exception
java.lang.RuntimeException: Failed to check session lock, aborting
        at dy.<init>(SourceFile:168)
        at dy.<init>(SourceFile:144)
        at ee.<init>(SourceFile:35)
        at net.minecraft.server.MinecraftServer.c(SourceFile:139)
        at net.minecraft.server.MinecraftServer.d(SourceFile:130)
        at net.minecraft.server.MinecraftServer.run(SourceFile:186)
        at bm.run(SourceFile:480)

``` 

What would I need to do so that I can issue this without. Thanks :P Much appreciated.

---

### Post by risegeek on 2010-10-11
I am stuck here guys :(

---

### Post by WRDN on 2010-10-11
You appear to be running "minecraft.jar" from a place you don't have permission to write to, hence "java.io.FileNotFoundException: server.log (Permission denied)".

The "server.log" file will be created in the same directory as the jar file.
Copy minecraft.jar to your home folder, then try running it.

---

### Post by wkhasintha on 2010-10-11
You don't have access to server.log file. change file attributes if you can or move the file to ~.

---

### Post by WRDN on 2010-10-11
> **wkhasintha said:**
> You don't have access to server.log file. change file attributes if you can or move the file to ~.

"java.io.FileNotFoundException" - the file doesn't exist.
Minecraft server creates the file on startup, along with any other files it needs, that don't exist currently.

---

### Post by risegeek on 2010-10-12
I've moved it to my home directory, same problem. These files do exist I believe;

```
sam@server1:/home/minecraft$ ls
banned-ips.txt      Minecraft-Overviewer  server.log.1       util.py
banned-players.txt  minecraft_server.jar  server.log.lck     util.pyc
blockcounter.py     nbt.py                server.properties  world
chunk.py            nbt.pyc               setup.py           world2
chunk.pyc           ops.txt               template.html      world.py
COPYING.txt         quadtree.py           terrain.png        world.pyc
flatgrass           quadtree.pyc          textures
gmap.py             README.rst            textures.py
minecraft.jar       server.log            textures.pyc

```

Sorry for the file cluster, I was fooling around with overviewer y/day.

---

### Post by combat_wombat27 on 2010-10-23
I HAVE THE SOLUTION YOU ARE LOOKING FOR!!!
had the same problem and now it works perfectly

btw NEVER RUN THE GAME SERVER AS ROOT OR SUDO IT.. bad bad


go to the folder where the minecraft server is and run this command

sudo chmod -R 0777 *

---

### Post by blindenvy on 2010-11-10
> **combat_wombat27 said:**
> I HAVE THE SOLUTION YOU ARE LOOKING FOR!!!
had the same problem and now it works perfectly

btw NEVER RUN THE GAME SERVER AS ROOT OR SUDO IT.. bad bad


go to the folder where the minecraft server is and run this command

sudo chmod -R 0777 *

I am having the same issue, the above did not fix the problem.

---

### Post by wkhasintha on 2010-11-11
> **WRDN said:**
> "java.io.FileNotFoundException" - the file doesn't exist.
Minecraft server creates the file on startup, along with any other files it needs, that don't exist currently.

oh my mistake sir [IMG]http://ubuntuforums.org/images/icons/icon14.gif[/IMG]

---

### Post by combat_wombat27 on 2010-11-12
> **blindenvy said:**
> I am having the same issue, the above did not fix the problem.

Can you please go through and describe your problem, perhapse past the log you get from trying to run the minecraft server so that I can see what would be the problem?

---

