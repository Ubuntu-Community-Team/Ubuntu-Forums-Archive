---
title: "Black Blank Screen Woes"
date: 2009-09-14
forum: New to Ubuntu
---

### Post by TomGroff on 2009-09-14
Hi all,
 
I messed up big time.
 
After reinstalling Hardy and upgrading to Intrepid I attempted to change my screen resolution.  Got a blank screen with a message saying that the resolution was invalid. (Or something similar.)
 
I get the same blank black screen and error everytime I log in.
 
Before logging in the I can get an option to log_in in a terminal mode.
I assume that this is where I need to be to fix the problem.
 
Can someone tell me what command I need to use to restore my graphics resolution to something visible?
 
Thank You in advance
 
-Tom-

---

### Post by NightwishFan on 2009-09-14
What is the error message?

First check if Ubuntu has a recovery mode in Intrepid. (I forget) It is at the OS selection screen, you may need to press ESC to view it if Ubuntu is your only OS. From there you can use the xfix option. I am not sure if this exists in Intrepid, I know it is in Jaunty. If not:

Try this command:

```
sudo dpkg-reconfigure xserver-xorg
```

Answer the default answers, unless you know what else would be appropriate.

---

### Post by zerhacke on 2009-09-14
sudo dpkg-reconfigure xserver-xorg

Nightwish beat me to it.

---

### Post by TomGroff on 2009-09-14
Intrepid has a pull down at the bottom left of the log-in screen. One of the items listed is restore last used configuation. Unfortunately I rebooted and tried to log in several times. So I would assume that the last saved was bad as well.
 
Ubuntu is the only OS on my PC at home. I am using my work PC to post this message so I cannot try your suggestions until tonight.
 
I'll give: sudo dpkg-reconfigure xserver-xorg
a try.
 
Thanks!
 
P.S.  Guess I'll have to print a hard copy to carry home.  :D

---

### Post by jnorthr on 2009-09-14
any chance you can try running your live CD, just to see if it something about your install that i not right ? You only need to run the live-CD while you are fixing this problem, you don't wnat to do a full install do you ? No doubt you've made a lot of backups for your data, so a full re-install might fix it all.  :)

---

### Post by TomGroff on 2009-09-14
Well I'm home now with a borrowed Windows Laptop.
Tried the Sudo... Thing. Not sure what the heck it did. But no change when I try to log in.
 
The message says... Input Signal our of Range.
 
I hope I do not have to do a full reinstall from CD. *Grump* *Grump*
 
Okay... Booted to the install CD.  Desktop came up just fine.  Removed the CD and rebooted... "Input Signal our of Range"  Yet again.  *Sigh*

---

### Post by NightwishFan on 2009-09-16
Ok, perhaps this will work for you.

When you are on the live cd, can you access the hard disk of your installed Ubuntu (the broken one)?

Perhaps copying the working Xorg.conf from the live CD into your installation will fix the problem.

Just mount the Ubuntu drive, and run this (in a terminal on the live CD) Make sure you spell everything right, even capitals.
```
sudo cp /etc/X11/xorg.conf /media/disk/etc/X11/xorg.conf
```

Then reboot into your system.

---

