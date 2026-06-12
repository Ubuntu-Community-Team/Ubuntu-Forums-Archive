---
title: "Freezing on Bootup"
date: 2010-06-10
forum: New to Ubuntu
---

### Post by noworldorder on 2010-06-10
revently upgraded to 10.04 Ubuntu

yuck...  Every now and then my system boots up, I log in but then...

It goes past a screen requiring my permission (for a script I have written)  boots up to the desk top and then nothing can be activated by my mouse!  I have to shut down by holding down the power button!

This has resolved itself by me logging in in safe mode, doing nothing, and rebooting normally - but not this time.  I can't do anything in Ubuntu and am asking for you help from Windows!  Help please.

I recently upgraded to 10.04.   The problem did not show up  right after the upgrade; however, it never happened in 9.10.

Thanks - Chris

---

### Post by nhasian on 2010-06-10
are you using a mouse or a touchpad?

[https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/546503](https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/546503)

> **noworldorder said:**
> revently upgraded to 10.04 Ubuntu

yuck...  Every now and then my system boots up, I log in but then...

It goes past a screen requiring my permission (for a script I have written)  boots up to the desk top and then nothing can be activated by my mouse!  I have to shut down by holding down the power button!

This has resolved itself by me logging in in safe mode, doing nothing, and rebooting normally - but not this time.  I can't do anything in Ubuntu and am asking for you help from Windows!  Help please.

I recently upgraded to 10.04.   The problem did not show up  right after the upgrade; however, it never happened in 9.10.

Thanks - Chris

---

### Post by noworldorder on 2010-06-10
yes I have a touchpad and it is HP.  

I did something very scientific.  I touched all of my keys - pressed them like  a monkey - and it works.

But if it is the bug you mention then why does it go past the permission screen I have that is accociated with a scrip on startup?

Thanks

---

### Post by nhasian on 2010-06-10
yeah its a weird bug.  the keyboard and mouse work at the login screen but after you type in your password and log in successfully, then the keyboard and touchpad stop functioning.  please mark that the bug affects you too in launchpad so you will be alerted to the resolution.

---

### Post by noworldorder on 2010-06-10
I can use function f6 to lock my computer and whern it is unlocked it is working.

Do these bugs usually get resolved?

And does this only affect 10.04?

And can you understand why it would go past a permission screen for a script?

Thanks for your help.

---

### Post by noworldorder on 2010-06-10
I discovered the pressing alt + o restores normal function to the mouse.

---

### Post by nhasian on 2010-06-10
what does alt-o do?

> **noworldorder said:**
> I discovered the pressing alt + o restores normal function to the mouse.

---

### Post by noworldorder on 2010-06-10
I have no clue - I am a newbie.  I discovered that it resores the mouse to normal function after I press it.

I can't seem to find any function that it has.  ?????

---

### Post by noworldorder on 2010-06-12
well I don't think I actually have the bug related to the touchpad.  I removed the script that I wrote from the startup.  Now when the computer starts it works fine.  I can run the script manually and everything is fine.

So why would a script have the effect of allowing nothing to be activated by my  mouse?  This is the script:

#!/bin/sh
mount -t smbfs //192.168.1.104/MediaShare /mnt/MediaShare 
mount -t smbfs //192.168.1.104/Backup /mnt/Backup

and this is what I enter in startup to make it run on bootup:

  	 	 	 	 	 	  gksudo /home/chris/Documents/SCRIPTS/automount.sh
 

Can anyone understand why this script would suddenly be causing this problem?

Thanks

---

