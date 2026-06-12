---
title: "virtualbox"
date: 2010-07-11
forum: New to Ubuntu
---

### Post by DarinB on 2010-07-11
i get **no medium found.**..even though the xp cd is in the cdrom. 
i am trying to set up virtualbox on a friends laptop clevo D900T...
I've been searching the net is seems to be a common problem but no real solutions. he is running Linux Mint 9....lucid lynx with a nicer theme (BTW the windows buttons on the right LOL)
Any Ideas?????

---

### Post by gdonwallace on 2010-07-11
Check under storage device and make sure that the CD is set to Pass-through.  That way the virtual CD will read from the real CD.

Also, if the hard drive is ext4, there is a known bug in virtual box that they are currently working on.  To get around it, go into the settings for the virtual hard drive and make sure that the is a check in the i/o box.  That should fix any problems as well.

good luck.

---

### Post by diablo75 on 2010-07-12
You have to make sure that virtualbox knows that you want the DVD drive in your computer to be used within your system.  Check your VMs settings to see what it's mounting for Primary and Secondary IDE devices.  It might not be mounting any CD-ROM device at all or is mounting an ISO file instead of discs you put in your drive.  You can switch your defaults around easily.

---

