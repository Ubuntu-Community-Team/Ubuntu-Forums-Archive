---
title: "Dell Mini 12, cannot run avant window manager"
date: 2009-09-01
forum: New to Ubuntu
---

### Post by balexander04 on 2009-09-01
I am trying to make my Ubuntu look like a mac, but I am having trouble with the Avant Window Manager dock starting. I have run into several errors and have searched about to fix them, and for the most part I have fixed them, but there is one that has halted my progress. I cannot run the Avant Window Navigator, I get an error message every time: Warning: Screen isn't composited. Please run compiz (-fusion) or another compositing manager. The problem is that I am not sure if my Dell Mini is capable of running this. I do not have the ability to adjust the the visual affects, because there is no tab in the "System>Preferences>Appearance" menu. The fact that I do not have the ability to adjust my visual affects, makes it difficult to find the simple solution. I have done my best to search for a solution, would anyone help me, please. I am fairly new to Ubuntu, and I would be most appreciative of any help offered.

---

### Post by karamu on 2009-09-01
You can get AWM to run without Compiz- you need to set Metacity (the default window manager) to composite.

You do this by going into the configuration editor- to find it you need to edit the menus to list the program- right click on the "Applications" button in the top left and chose edit menus.

In the "System tools" section you will find "Configuration Editor"- enable this then from the application menu you can start it (there may be a command line way to do this but I don't know of it).

Now, from Configuration Editor you can find Metacity (in the apps section) and set Compositing.

Let me know if my explanation doesn't make sense.

---

### Post by Bölvaður on 2009-09-01
ok lets turn our noodles in our head on full rotation.

What you want: AWN
What does AWN need: a composite window manager
What do you need for that: A decent graphic card (and driver for it)

to have it simple:
AWN &#8594; Compiz &#8594; Graphic driver &#8594; Graphic card


The driver is where it all fails.

"Video Intel 500 GMA (Intel Integrated only)"
(*note that Im saying the driver fails not the built in card)

[This is another guy with the same computer as you have]("http://ubuntuforums.org/showthread.php?t=1014534")


Now: how to solve the issue?
[URL="http://ubuntuforums.org/showthread.php?t=1130582"]
Follow the optimal way in this thread[/URL] and up that kernel you install every time you want to have a working driver :)
I hope the Intel problem will be fixed in next release of ubuntu because this wasnt a problem before this release (a dark half a year for some ubuntu users)

---

### Post by karamu on 2009-09-01
I know that there are issues with the graphics chipset in the Mini 12 but you don't actually need Compiz to run AWN- Metacity does the job fine- I have it running on my desktop Dell using the onboard graphics.

---

