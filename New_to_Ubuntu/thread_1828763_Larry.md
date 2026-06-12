---
title: "Larry"
date: 2011-08-19
forum: New to Ubuntu
---

### Post by lbenn1950 on 2011-08-19
Okay here goes. First I had an abject failure trying to install ubuntu 11.04 and 10.10 on my laptop. I have a Dell Inspiron 1000. Error msg. unrecoverable error on the Ubuntu splash screen. Prior to that I got an error msg. in dos something about firmware but it only lasted a couple of seconds and I can't read and retain that quickly. Next step was downloading the windows installer on my PC AMD 64 3000. It seemed to go through the process smoothly but when I went to reboot and pick the option on the boot screen there was not a Ubuntu option. I tried to uninstall the program but was denied access. Now I am a little upset. So I used the cd that I downloaded and booted from that. Now my question is can I install from the cd and still keep my windows xp pro version or does the install wipe and reformat my drive? I am about ready to give up on the easy to use Ubuntu. Please any help would be appreciated.

---

### Post by spiky001 on 2011-08-19
Are you trying to install wubi (within windows) or dual boot along side windows. What website were you following

---

### Post by halfmind on 2011-08-19
I identify strongly with the abject failure and frustration bits. There seems to be a fairly steep learning curve... Stick with it, though. If nothing else, it'll give you hours of emotionally cathartic activity... 
     I can't help if it's a hardware/firmware issue, but I do have a recommendation for your installation question: If you're not using the Ubuntu LiveCD, do. ([http://www.ubuntu.com/download](http://www.ubuntu.com/download)). Select the option to "try it from a USB stick or CD". The LiveCd, after it boots, will offer you the option of playing with Ubuntu but not installing it, or installing it. Then it will ask if you'd like to wipe your current OS, or if you'd rather use a dual-boot configuration. Select the dual-boot option, and the CD will do the rest. It's pretty not-frustrating...

---

### Post by lbenn1950 on 2011-08-19
Using the windows installer within windows. Everything seemed to go well but when I re-booted there was not a boot option for Ubuntu

---

### Post by Rex Bouwense on 2011-08-19
I read you post with interest as I also have a Dell Inspiron 1000.  I am running Lucid Lynx (10.04) on it as a sole operating system.  I did add a 256 RAM chip to bring the total up to 512 so I can get a decent speed out of it.  I have a couple of web sites for you to read if you are wanting to dual boot, but first if you are going to install Ubuntu inside of Windows using WUBI you should know that it is not intended to be a long term install.  It should be used to introduce one's self to the OS.  It is a little slow but you will still have the Ubuntu experience.  A better choice would be a side by side installation which you can do from the CD that you downloaded and hopefully ran an MD5Sum check on.
Here are the web sites:
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
[https://help.ubuntu.com/10.04/switching/C/dualboot.html](https://help.ubuntu.com/10.04/switching/C/dualboot.html)
[http://ubuntuforums.org/showthread.php?p=10257675](http://ubuntuforums.org/showthread.php?p=10257675)
Enjoy.

---

### Post by anewguy on 2011-08-19
+1 -wubi is really only meant for a simple test drive - just check the forum for all the problems people have who try to use it in place of a "real" install.

We should probably know the specs on your computer - we see you mentioned AMD 64 3000.  How much memory?  What size of hard disk?  Are you running a 64 or 32 bit version of Windows?  Are you trying to install the 32 or 64 bit version of Ubuntu?

The answers to these questions really are needed before we can give you good advice as all of those things play into the install.

For you and for others reading this thread and are tempted to just put in the LiveCD, boot in and do the install choosing the option to keep Windows and share the disk with Ubuntu.  Before you EVER shrink the size of the Windows partition, ALWAYS defrag the disk at least once - 2 or 3 times, believe it or not, is actually better.  If your disk is fragmented when you go ahead and shrink the partitiion, there is a higher risk of data loss.

Dave ;)

---

