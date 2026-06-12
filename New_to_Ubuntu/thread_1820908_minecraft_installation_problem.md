---
title: "minecraft installation problem"
date: 2011-08-08
forum: New to Ubuntu
---

### Post by Schweinessener on 2011-08-08
ive installed the java runtime and all, and to run minecraft, i right click the .jar and click 'open with java 6 runtime'
i get this error:
'The file '/home/george/Desktop/minecraft.jar' is not marked as executable.  If this was downloaded or copied from an untrusted source, it may be dangerous to run.  For more details, read about the executable bit.'
what am i doing wrong?

---

### Post by Schweinessener on 2011-08-08
alright ive fixed that. now i get this error after i log in to minecraft:

'      Minecraft has crashed!      
      ----------------------      

Minecraft has stopped running because it encountered a problem.

If you wish to report this, please copy this entire text and email it to [email]support@mojang.com[/email].
Please include a description of what you did when the error occured.



--- BEGIN ERROR REPORT a1dce528 --------
Generated 8/8/11 9:12 AM

Minecraft: Minecraft Beta 1.7.3
OS: Linux (amd64) version 2.6.38-10-generic
Java: 1.6.0_26, Sun Microsystems Inc.
VM: Java HotSpot(TM) 64-Bit Server VM (mixed mode), Sun Microsystems Inc.
LWJGL: 2.4.2
[failed to get system properties (java.lang.NullPointerException)]

java.lang.IllegalStateException: Only one LWJGL context may be instantiated at any one time.
    at org.lwjgl.opengl.Display.create(Display.java:846)
    at org.lwjgl.opengl.Display.create(Display.java:784)
    at org.lwjgl.opengl.Display.create(Display.java:765)
    at net.minecraft.client.Minecraft.a(SourceFile:294)
    at net.minecraft.client.Minecraft.run(SourceFile:716)
    at java.lang.Thread.run(Thread.java:662)
--- END ERROR REPORT a2bcbe25 ----------'

---

### Post by Sam White on 2011-08-08
Right click and choose properties, then choose the middle tab and check the box that says 'allow executing the file as program' or something along those lines.

Alternatively, open a terminal in that directory and run a

chmod +x <name of java file goes here>

Then try again

Sam

EDIT: Haha, you beat me to it. Not sure about the next issue. Sorry.

---

### Post by slugs on 2011-08-08
Try running this command in the terminal:
```
chmod u+x /home/george/Desktop/minecraft.jar
```

This command makes minecraft.jar executable so now it should work.

EDIT: Sorry, someone already said this.

---

