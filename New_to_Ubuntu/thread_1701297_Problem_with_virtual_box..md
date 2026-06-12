---
title: "Problem with virtual box."
date: 2011-03-06
forum: New to Ubuntu
---

### Post by abnordude on 2011-03-06
I used my virtualbox to install windows Xp for downloading a large file through the use of IDM.
It is an iso image that I need to burn it to a disk. But when I insert a blank disc, windows doesn't read it [linux does].
So, is there any way to move the downloaded iso into linux. Please help me.

---

### Post by thane1 on 2011-03-06
If I understand your Virtualbox setup correctly, you have Ubuntu set up as your vbox host machine and have set up XP as your vbox guest machine.  There are a few ways, that you can transfer the file to burn with Ubuntu. You can transfer files through virtualbox's shared files feature or you can install/set up samba on its own to share files.  A large enough usb stick could also work depending on the size of your file. Are you sure the file downloaded properly?
 
     The preferable method though, might be to set up your real hardware burner to work with XP, if that hasn't already been done.  You will probably need to set it up manually to work with XP, as it won't be detected by default.  Your secondary host device needs to be changed to your real optical drive.  Try the ubuntu forums virtualization forum here for help:

[http://ubuntuforums.org/forumdisplay.php?f=308](http://ubuntuforums.org/forumdisplay.php?f=308)

or the Virtualbox forums and the Virtualbox manual can help.  Also I'm assuming you already have guest extensions installed.  Virtualbox extensions would be a good idea as well, if you want to plug in any usb devices.  Cheers

---

### Post by thane1 on 2011-03-06
By the way the Oracle VM Virtualbox User Manual section, which deals with setting up a Windows guest hardware burner is (for Vbox version 4) section 5.9 on page 81.  Cheers

---

### Post by abnordude on 2011-03-06
Hey Thnkx for the tip. It worked. Thnk u so much.

---

### Post by thane1 on 2011-03-06
Glad it worked for you.  Cheers

---

