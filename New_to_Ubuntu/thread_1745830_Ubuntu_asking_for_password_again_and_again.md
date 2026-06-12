---
title: "Ubuntu asking for password again and again"
date: 2011-05-01
forum: New to Ubuntu
---

### Post by MarSand on 2011-05-01
I'm absolutely new to linux and ubuntu. I'm not a computer expert but I can follow instructions. I just installed Ubuntu 10.10 in a Compaq Presario 4000. After installation the screen went blank. I restarted the computer manually and  Ubuntu started just fine, I had access to the applications and internet but when I tried to shut down the screen went blank and the keyboard was flashing.

I did this a couple of times, but now the situation has changed: When I turn on the computer I'm asked for the password, I type it and then I see the Ubuntu Desktop but the screen goes blank right away and I 'm asked for the password again. And as long as I type the password I get to the desktop, then the blank screen, then the password request. Again and again.

Anyone out there that can help me?????

Thanks

---

### Post by Rockky on 2011-07-05
I am also having the same problem . When I enter my password while booting up, it shows screen with system loadings for a split second and takes me back to password entry screen .
I recently installed Apache server , php , maven and subversion utilities around 4-5 days back. 
Then I also got my wireless card (Broadcom 4328) working properly by installing bcmw utilities .
I also remember that I was very low on space , probably 100 MB was left .Please help me out on this. I tried deleting some files from recovery mode as well

---

### Post by autonym on 2011-07-05
Try this and see if it helps; Applications -> (search for) Screensaver -> Untick "Activate screensaver when computer is idle" and "Lock screen when screensaver is active".

I hope that helps...

---

### Post by Rockky on 2011-07-05
hmm...can u help me with my problem .i am not able to boot up . I mean it asks for password again and again and I am NOT directed to desktop :(

---

### Post by autonym on 2011-07-06
> **Rockky said:**
> hmm...can u help me with my problem .i am not able to boot up . I mean it asks for password again and again and I am NOT directed to desktop :(

Humm... I don't know what that can be. If it was me then I would take the easy way out. If I was sure that I've entered the right password I would format the root partition. When I installed root again I would as a (ironic) safetymeasure untic the "ask for password on startup" option.

I'm sorry I couldn't be of more help.

---

### Post by hakermania on 2011-07-06
Are you sure you didn't unistall nautilus?

---

### Post by SeijiSensei on 2011-07-06
At boot, choose rescue mode and open a root shell.  Go to /home and rename your home directory with "mv username username.old".  Reboot.  Your home directory will be recreated with the default settings.

If you don't get the grub menu at boot, hold down the shift key while the machine starts.

---

### Post by wep940 on 2011-07-06
+1 on the unintentional delete of Nautilus.  If you deleted it, you will have those exact same symptoms (I know - I was dumb enough to try this!).  Someone may know another way, but I had to completely reinstall to get things back.

The other thing that is possible is that the video driver that X is setting up is not compatible - for example, your video adapter may not support Compiz or Unity.  I ran into this as well, with the resulting same symptoms - I would log in, the system would try to run my defaults which included Compiz (and Unity in 11.04), find out I didn't have the resources and return to the password screen because it was unable to start any video for the desktop.  I would try editing the boot line when grub comes up and add the following to the boot line:

nomodeset, VGA=722, acpi=off

See if that helps.  If it does, just keep rebooting and at the grub menu edit the boot line and remove one of the three things added until it doesn't work anymore - at that point you'll know which one you need and we can help you make it a permanent change.

If that doesn't work, then log in to the command line (recovery mode).  Then try sudo startx - if it kicks up some error messages write them down and post them back here.

---

