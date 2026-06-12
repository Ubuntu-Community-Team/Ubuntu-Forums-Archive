---
title: "Booting problem."
date: 2010-07-12
forum: New to Ubuntu
---

### Post by cr4321 on 2010-07-12
Gentlemen,

I have a disk with multiple partitions. Primary partition has Win-xp, and one of the extended partitions has Ubuntu 10.04. The default boot was set to this. This system has been updated 2 weeks back and has been set up quite to my liking, with many useful programs downloaded and installed.

It was working fine all these days.

Today I used StartUpManager to change the default boot to Windows. (If I remember right, I also ticked on the option mentioning about showing splash screen)

On restarting the computer, the menu is coming up as usual, and all other systems (including windows and other linux distros) are working alright. However, Ubuntu 10.04 does not boot at all. Even the recovery mode is not working showing similar symptoms. When booting into Ubuntu 10.04, the screen goes blank, the hard disk keeps reading - then a band of green is displayed (about 1" at the top of the monitor, progressively) and the hard disk reading stops. The system goes dead.

Have I botched up? Is there any recovery from this? 

Would like to try out some suggestions. I do not know command line operations.

Thanks in advance.

cr4321

---

### Post by Penguin Guy on 2010-07-12
Looks like it's some kind of graphics issue. If you can turn off the splash screen somehow that should fix it.

Boot into a live CD, open the terminal and post back the results of:
```
ls /boot/grub/
```
This should tell us what kind of setup you're using (grub or grub2).

---

### Post by cr4321 on 2010-07-13
> **Penguin Guy said:**
> Looks like it's some kind of graphics issue. If you can turn off the splash screen somehow that should fix it.

Boot into a live CD, open the terminal and post back the results of:
```
ls /boot/grub/
```This should tell us what kind of setup you're using (grub or grub2).

Yes, it certainly is a graphic issue, as the file system shows ok, and the green band is consistent (briefly changes when "esc" or "return" is pressed and appears again) It looks like some message I am not able to see.

As for booting with live cd and result of the terminal command is just : grubenv

Is this grub2?  Anyway, it is not a grub issue, since other systems are functioning ok.

Thanks so far... and let me keep trying!

---

### Post by oldfred on 2010-07-13
On the grub menu press e for edit and replace the quiet splash with nomodeset and try booting. Without quiet & splash you may see what command is causing the error. nomodeset may prevent a change in the video mode.

---

### Post by cr4321 on 2010-07-13
:DThanks, it got solved - half by accident, half by hitting in the dark!

After I realised that it could be waiting for an "input" from me, I tried out various key - and "s" for skip worked and the system is now gung-ho! I must thank you for guiding the thought process! Thanks.
(Let me now find where to mark this as [solved])

---

