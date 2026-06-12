---
title: "grub.cfg not found, though it is there."
date: 2010-08-21
forum: New to Ubuntu
---

### Post by JamButty on 2010-08-21
Did routine update with about 5 items, all something like "Linux headers". It requested reboot. After all I had was black screen with

Gnu Grub version 1.98-ubuntu7
grub>

I have XP on one partition and Ubuntu LL on the other. I cannot get to the boot menu.

I spent two days communing with the Grub and Grub2 manuals, exploring from the prompt.
The grub.cfg file is exactly where it should be in /boot/grub
I've gone over every line and it all looks right.
I can enter the commands in grub.cfg at the grub prompt for the appropriate linux and Windows boot sections of the boot menu it should build and display and boot into each of those systems, but still whatever should be looking for grub.cfg on boot does not, or does not find it and so it just displays the grub command line prompt.

sudo update-grub from the Gnome terminal does not change this.

Anyone have experience with this? thanks

---

### Post by uRock on 2010-08-21
Have you tried booting the LiveCD and running the update-grub command?

---

### Post by dagdeniz on 2010-08-21
I haven't experienced but it seems possible. Yes, grub.cfg is still there but the kernel may not be still there, may it be replacd by an upgraded kernel? So if grub looks for kernel, e.g., 2.6.32 and cannot find it, grub rescue screen may meet you. I'd try to boot manually before doing something else (at least to know if I'm doing it right).

To do that, you must know the root partition, the exact path to the kernel and root directory. It's normally like this:
grub> linux /boot/vmlinuz root=/dev/sdx
grub> initrd /boot/initrd
grub> boot
replace /boot/vmlinuz and /boot/initrd with the exact paths. After succeeding in booting, you can refer to manual editing instructions in gnu grub manuals. The word "linux" may be replaced with "kernel" and sdx with hdx. 

For more info, look here: 
[http://www.gnu.org/software/grub/manual/grub.html#GNU_002fLinux](http://www.gnu.org/software/grub/manual/grub.html#GNU_002fLinux)
and compare to here:
[http://orgs.man.ac.uk/documentation/grub/grub_4.html](http://orgs.man.ac.uk/documentation/grub/grub_4.html)

---

### Post by JamButty on 2010-08-21
Yes, I am booting manually, as I wrote. It allows me to continue, so I am delaying a wipe and reinstall for now (a bit of a pain for the Linux side, an ENORMOUS pain for the XP side)
All files are where they should be: vmlinuz and initrd files in /boot. UUID values are kosher. If they were not, I would get the boot menu and THEN errors upon choosing a menu selection.

There is some other linkage that is missing that the  Grub2 manual does not describe, as far I have understood at least, something between BIOS and grub.cfg where the world collapses.

@urock - have not yet - but unclear how that is different from sudo update-grub from the Gnome terminal - will try.

thanks for responses.

---

### Post by phillw on 2010-08-21
Hi,

welcome to the forum.

I don't know what level of experience you have with using the terminal, but if your GRUB is messed up with that error you may well find [ You did What?!!](http://forum.phillw.net/viewtopic.php?f=4&t=35) should get it sorted for you.
As it also forces Grub to update, it will find your windows area.

Regards,

Phill.

---

### Post by JamButty on 2010-08-21
SOLVED!

I did sudo upgrade-grub before. I needed upgrade-grub2.  Probably the same error was somewhere in the coding for the routine upgrades that started this.  All is normal now.

Thanks.

---

### Post by libssd on 2010-08-21
As you have figured out, somewhere in your update process, it changed from  "legacy" grub to grub2.

There is a plethora of information here: [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

