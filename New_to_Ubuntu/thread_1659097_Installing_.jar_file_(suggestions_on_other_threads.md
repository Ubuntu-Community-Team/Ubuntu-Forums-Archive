---
title: "Installing .jar file (suggestions on other threads failed)"
date: 2011-01-03
forum: New to Ubuntu
---

### Post by AliceKingsley on 2011-01-03
I have looked through all the old threads I could find, but I cannot get a .jar file to install. I entered the following: 
```
java -jar ~/Games/Minecraft.jar
```
This is the result: 
```
Exception in thread "main" java.awt.HeadlessException
        at java.awt.GraphicsEnvironment.checkHeadless(GraphicsEnvironment.java:173)
        at java.awt.Window.<init>(Window.java:437)
        at java.awt.Frame.<init>(Frame.java:419)
        at net.minecraft.LauncherFrame.<init>(LauncherFrame.java:17)
        at net.minecraft.LauncherFrame.main(LauncherFrame.java:137)
        at net.minecraft.MinecraftLauncher.main(MinecraftLauncher.java:13)

```
I then extracted the .jar and tried to just run the applet: 
```
java ~/Games/Minecraft/Minecraft/java.policy.applet
```
Which returned:
```
Exception in thread "main" java.lang.NoClassDefFoundError: /home/alicekingsley/Games/Minecraft/Minecraft/java/policy/applet
Caused by: java.lang.ClassNotFoundException: .home.alicekingsley.Games.Minecraft.Minecraft.java.policy.applet
        at java.net.URLClassLoader$1.run(URLClassLoader.java:217)
        at java.security.AccessController.doPrivileged(Native Method)
        at java.net.URLClassLoader.findClass(URLClassLoader.java:205)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:321)
        at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:294)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:266)
Could not find the main class: /home/alicekingsley/Games/Minecraft/Minecraft/java.policy.applet. Program will exit.
```

In one of the threads about .jar issues someone asked for the output of this command:
```
jar -tf ~/Games/Minecraft.jar
```
Which was:
```
META-INF/MANIFEST.MF
META-INF/MOJANG_C.SF
META-INF/MOJANG_C.DSA
META-INF/
java.policy.applet
net/
net/minecraft/
net/minecraft/dirt.png
net/minecraft/favicon.png
net/minecraft/GameUpdater$1.class
net/minecraft/GameUpdater$2.class
net/minecraft/GameUpdater$3.class
net/minecraft/GameUpdater$4.class
net/minecraft/GameUpdater.class
net/minecraft/Launcher$1.class
net/minecraft/Launcher$2.class
net/minecraft/Launcher.class                                         
net/minecraft/LauncherFrame$1$1.class                                
net/minecraft/LauncherFrame$1.class                                  
net/minecraft/LauncherFrame.class                                    
net/minecraft/LoginForm$1.class
net/minecraft/LoginForm$2.class
net/minecraft/LoginForm$3.class
net/minecraft/LoginForm$4.class
net/minecraft/LoginForm$5.class
net/minecraft/LoginForm$6.class
net/minecraft/LoginForm$7.class
net/minecraft/LoginForm$8.class
net/minecraft/LoginForm$9.class
net/minecraft/LoginForm.class
net/minecraft/MinecraftLauncher.class
net/minecraft/Util$OS.class
net/minecraft/Util.class
LZMA/
LZMA/CRangeDecoder.class
LZMA/LzmaException.class
LZMA/LzmaInputStream.class
```
I don't know if that's useful information, but I figured it wouldn't hurt to include it. 

I don't know if I even have java installed correctly, but I don't know how to find out. Attached is a screen shot of the result of searching for java within my installed packages. I don't know how to get my terminal to show that information. (There was a note on the download page that this program needs Sun Java.)

I assume that I'm missing something really basic, and I would really appreciate help figuring out what that is.

---

### Post by Vermind on 2011-01-03
The first exception tells me that you are running Minecraft with a headless JRE. This means that the Java you are using does not have GUI classes at all. Perhaps you need to install the openjdk-6-jre package?

---

### Post by AliceKingsley on 2011-01-04
That did it. Thank you so much!

---

