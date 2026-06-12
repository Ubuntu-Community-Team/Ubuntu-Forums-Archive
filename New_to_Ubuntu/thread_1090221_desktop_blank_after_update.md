---
title: "desktop blank after update"
date: 2009-03-08
forum: New to Ubuntu
---

### Post by suh on 2009-03-08
hi all
this is my first thread. i am not much aware with intricacies of getting help.
i am a new user of 64 bit ubuntu 8.04.  everything was great but when when i upgraded and rebooted my problems started. now when i start ubuntu my log in screen comes. after logging in the desktop has disappeared and only an orange blank screen is visible with white square on top left corner. i have not installed kde desktop yet and only using gnome. can anybody kindly help? how can i rescue my desktop? kindly suggest off line solutions b'coz my internet has still some issues.
i have installed and customized many applications on it.so i don't want to reinstall ubuntu once again.
thanks a lot

---

### Post by hello_kitty on 2009-03-08
I had what appears to be a similar problem when using kubuntu 6 months back.  Basically, once I enabled desktop effects (without proper drivers), I wouldn't get the desktop.  I would get the initial log-in screen and everything, but as soon as I submitted my info, the desktop would begin to load and immediately turn white, and go no further.  Again, this may not be the same issue as you (considering you are using gnome and not kde), and even if it is, I can't be much more help because I don't remember the fix.  LOL  It has been awhile!  But there IS a fix (config file I believe), and that is all I wanted to let you know.  Good luck!

---

### Post by tuesdaytaurus on 2009-03-08
Hi. I had the same problem recently. After an upgrade (about 10 days ago) my compiz stopped working and ALL Visual effects were reverted back to defaults. After many trial and error session, trying to get XServer and my NVIDIA Geforce Go 7300 card to play nicely with the NVIDIA 177 (recomended) driver, I finally got the Ubuntu NVIDIA 180.32 graphics driver installed. Everything seems to work now, but I still don't have Visual effects.

   > can anybody kindly help? how can i rescue my desktop? kindly suggest off line solutions b'coz my internet has still some issues

Suh, the simplest way I know is to restart you machine and press ESC when GRUB (boot loader) starts. This will give you startup options. 
**Select the topmost option that has "Recovery mode" or "Safe Mode" in brackets.**
This will give you a simple options menu that has the solutions to most common driver problems. 
**Select the bottom option: "Fix X-Server"** 
When you return to the menu, **Select the topmost option: "Boot Normally"**

This should get you back into the desktop. I suggest that, if you have a NVIDIA graphics card, you try the 180.32 driver. Otherwise search for "Xorg <Your Graphics card make and model>" to find relevant help forums.

---

### Post by suh on 2009-03-08
> **tuesdaytaurus said:**
> Hi. I had the same problem recently. After an upgrade (about 10 days ago) my compiz stopped working and ALL Visual effects were reverted back to defaults. After many trial and error session, trying to get XServer and my NVIDIA Geforce Go 7300 card to play nicely with the NVIDIA 177 (recomended) driver, I finally got the Ubuntu NVIDIA 180.32 graphics driver installed. Everything seems to work now, but I still don't have Visual effects.

   

Suh, the simplest way I know is to restart you machine and press ESC when GRUB (boot loader) starts. This will give you startup options. 
**Select the topmost option that has "Recovery mode" or "Safe Mode" in brackets.**
This will give you a simple options menu that has the solutions to most common driver problems. 
**Select the bottom option: "Fix X-Server"** 
When you return to the menu, **Select the topmost option: "Boot Normally"**

This should get you back into the desktop. I suggest that, if you have a NVIDIA graphics card, you try the 180.32 driver. Otherwise search for "Xorg <Your Graphics card make and model>" to find relevant help forums.

hi tuesdaytaurus
i tried as u told above but unfortunately it couldn't help. but i tried to check my /etc/x11/xorg.conf file. this file is simply not there.

---

### Post by suh on 2009-03-11
hello guys 
kindly help me in my issue. u can suggest online issues also. i will try to use them if my internet works. it works sometimes. but please help to get me out of this mess....
thanx

---

### Post by bailbath on 2009-03-11
Can you tell us your hardware?
Also you say that you have problems with the internet. If you were updating and lost connection that could have broke yr system.
Could you get into the rescue options from the grub menu?
Ian

---

### Post by rustutzman on 2009-03-11
> **suh said:**
> hi tuesdaytaurus
i tried as u told above but unfortunately it couldn't help. but i tried to check my /etc/x11/xorg.conf file. this file is simply not there.

/etc/x11/xorg.conf Should be /etc/X11/xorg.conf Notice the capital "X" Linux is case sensitive.

Russ

---

### Post by suh on 2009-03-12
> **rustutzman said:**
> /etc/x11/xorg.conf Should be /etc/X11/xorg.conf Notice the capital "X" Linux is case sensitive.

Russ

yes i saw it. there are many xorg.conf files in /etc/X11/ directory with xorg.conf.????????? extensions. here ???????? refers to some numbers.
these are probably backup files. i tried to reconfigure my Xserver by dpkg-reconfigure -phigh xserver-xorg command and reboot but it didn't help.

---

### Post by suh on 2009-03-12
> **bailbath said:**
> Can you tell us your hardware?
Also you say that you have problems with the internet. If you were updating and lost connection that could have broke yr system.
Could you get into the rescue options from the grub menu?
Ian

thanx bailbath for your interest.
i am using the following system:
Processor : AMD Athlon 64 X2 4800+
MB        : ASUS M2A-VM, chipset ATI, onboard graphics
Memory    : 2 GB DDR2 
In Dual(or rather triple) BOOT mode with Windows XP SP2 and Scientific Linux 5.1.
if you need any other information i will provide.

---

### Post by suh on 2009-03-12
> **bailbath said:**
> Can you tell us your hardware?
thanx bailbath for your interest.
i am using the following system:
Processor : AMD Athlon 64 X2 4800+
MB        : ASUS M2A-VM, chipset ATI, onboard graphics
Memory    : 2 GB DDR2 
In Dual(or rather triple) BOOT mode with Windows XP SP2 and Scientific Linux 5.1.
if you need any other information i will provide.

Also you say that you have problems with the internet. If you were updating and lost connection that could have broke yr system.

yes my internet connection was broken during update. but it was not a full system update. i was updating only selected packages. some of them were gedit and some files of gnome and other packages. i was able to reboot into the system after update. the problem started with 3rd and subsequent reboots. 

Could you get into the rescue options from the grub menu?
Ian

yes i tried rescue options . tried to fix xserver, also dropped root to shell and subsequently updated gedit again from root.

---

### Post by suh on 2009-03-12
[QUOTE=bailbath;6877254]Can you tell us your hardware?
thanx bailbath for your interest.
i am using the following system:
Processor : AMD Athlon 64 X2 4800+
MB        : ASUS M2A-VM, chipset ATI, onboard graphics
Memory    : 2 GB DDR2 
In Dual(or rather triple) BOOT mode with Windows XP SP2 and Scientific Linux 5.1.
if you need any other information i will provide.

Also you say that you have problems with the internet. If you were updating and lost connection that could have broke yr system.

yes my internet connection was broken during update. but it was not a full system update. i was updating only selected packages. some of them were gedit and some files of gnome and other packages. i was able to reboot into the system after update. the problem started with 3rd and subsequent reboots. 

Could you get into the rescue options from the grub menu?


yes i tried rescue options . tried to fix xserver, also dropped root to shell and subsequently updated gedit again from root.

---

