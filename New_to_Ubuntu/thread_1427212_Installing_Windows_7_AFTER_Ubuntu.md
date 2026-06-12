---
title: "Installing Windows 7 AFTER Ubuntu"
date: 2010-03-11
forum: New to Ubuntu
---

### Post by Arex Bawrin on 2010-03-11
Is this possible? All the tutorials I've searched for require Windows to be setup first to achieve a successful dual boot.

---

### Post by Running_Dualboot on 2010-03-11
I had windows 7 and used Wubi to dual boot Ubuntu 9.10 and win7. Im not sure if you can get win7 after ubuntu tho#-o

---

### Post by Mark Phelps on 2010-03-11
It's easier if you install Win7 first because GRUB will then detect it and add an entry for it.

When you install Win7 second, it will overwrite GRUB. You will then have to reinstall GRUB.  Once that is done, you will need to boot into Ubuntu, open a terminal, and enter "sudo update-grub" to have it rebuild your GRUB menu to add an entry for Win7.

---

### Post by TurnOfTide on 2010-03-11
Perhaps you can get what you want by running Windows 7 in Virtual Box.

---

### Post by HermanAB on 2010-03-11
Yup, dual booting is sooooo previous century.  Install Virtualbox or VMware Player and install Windows in that.  Then you can run Windows in a window where it belongs.

---

### Post by karthick87 on 2010-03-11
Yes you can install windows 7 after ubuntu using **Grub4Dos**..
See this [link]("http://ubuntuguide.net/how-to-install-windows-7-from-ubuntu-without-burnning-a-disc")

---

### Post by akand074 on 2010-03-11
You can install Windows 7 after ubuntu just fine. Just make sure it is installed on the right partition. After you install windows 7 you'll have to reinstall grub to see Ubuntu, take a look at this link on how to do that: 

[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD]("https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD")

Its just easier to install ubuntu after windows 7 because then Grub is installed automatically, with windows 7 it will overwrite grub and you'll have to manually reinstall it using the LiveCD, but I've done it plenty of times.

---

### Post by sandyd on 2010-03-11
if you only have the windows 7 recovery discs, installing windows from them will wipe out ubuntu.

---

### Post by undecim on 2010-03-11
You can do it, but it takes a bit more work.

First, you need to make space for Windows by using GParted from a live CD. Make sure you have anything important backed up before doing this though. If something goes wrong here, it can be ugly.

Then you need to isntall windows to the free space you made.

After installing windows, you need restore grub: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by Arex Bawrin on 2010-03-14
Thanks for the help everyone:) I'm only asking because my database class is shoving access down my throat, but the last time I had Windows 7 running I got a virus and it messed everything up. Maybe I'll just go to the lab to use access, as I am pretty happy with Ubuntu right now.

---

