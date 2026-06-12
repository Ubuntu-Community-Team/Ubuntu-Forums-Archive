---
title: "Black screen after install and power on"
date: 2010-02-13
forum: New to Ubuntu
---

### Post by soft-e on 2010-02-13
Hello everybody outthere,
 
I'm getting a black screen after I install ubuntu 9.10, then shutdown and then power the computer on. I've installed all the updates prior to shutting down. Here's what I found when I seached the internet. In this article, [http://www.insidesocal.com/click/2009/11/are-your-graphics-dead-in-ubun.html](http://www.insidesocal.com/click/2009/11/are-your-graphics-dead-in-ubun.html) the author Steven Rosenberg says this:
 
"The problem is with kernel mode setting, which is causing X to die.
To test whether or not the fix works, when you get to the GRUB screen, hit esc to stop the boot, then go arrow down to the kernel boot line, type e to edit it and add the following to the end (or after the ro ... both work for me):
i915.modeset=0
Then type b to boot."
 
Now do I get to the GRUB screen. I'm staring at a black screen at the moment. How will I recognize the "Kernl boot line" that Steven is talking about. 
 
I've verified on ubuntu.. [http://www.ubuntu.com/testing/karmic/alpha6](http://www.ubuntu.com/testing/karmic/alpha6)
Here's what they have to say:
"Some users with Intel video chipsets will experience a black screen on reboot after install because the fbcon module is not being loaded. As a workaround, users can boot with the i915.modeset=0 option. Investigation of this issue is ongoing. (431812)"
 
Please let me know what to do here. I have a feeling I'm having a similar problem. 
 
-soft-e

---

### Post by patchwork on 2010-02-13
Upon restart, immediately after the BIOS screen runs, then screen will go mostly blank except for a the words "GRUB Loading".   Hold down the SHIFT button during this time, and you should be directed to a menu.   Each of the menu options is a boot line.  Select a bootline, and press 'e' to edit.  From there you can try to add your modeset command.

I don't have an intel graphics card, so unfortunately I haven't had any experience with this issue.

---

### Post by Julita on 2010-02-14
Hi! I have an Intel card, and I was able to boot after adding to the kernel line 
```
ro quiet splash nomodeset
``` Try that!

---

### Post by soft-e on 2010-02-15
Hello patchwork and Julita,
 
With your help, I've been able to sucessfully resolve my problem. I was able to press shift key down to be able to edit my "grub" and boot again. Then I edited the /boot/grub/grub.cfg and added "ro quiet splash nomodeset" and everything seems to be working fine now. My only question is, that I don't see a /boot/grub/menu.lst file. As per all the information on the internet, the is file that I need to be editing to make my changes to grub permanent.  Is grub.cfg the equivalent of menu.lst? Also, what if my grub gets updated later through automatic updates. Then my changes might get erased. How should I handle that.

---

### Post by Julita on 2010-02-16
NO! Don't do that!!! It may harm your system! The file that you need to edit is /etc/default/grub there, you have to find the line
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" (instead of "quiet splash" you may have something else; ) you have to edit the line so that it looks like
GRUB_CMDLINE_LINUX_DEFAULT="ro quiet splash nomodeset"
Save/exit the file and run the command
update-grub from terminal. By this, you can update grub to a new version and the configuration will be unaffected. If you edit grub.cfg, the changes after update will be lost. At the beginning of grub.cfg it is explained why you should not edit the file. In short, the system does it for you after configuration of (in your case) /etc/default/grub.

---

### Post by soft-e on 2010-02-21
Thank you. I had saved a copy of the original grub.cfg, so I copied that back into /boot/grub and made changes to /etc/default/grub and ran update-grub and everything works fine now.

---

