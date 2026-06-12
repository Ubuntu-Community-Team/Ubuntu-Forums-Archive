---
title: "Boot then blank screen; no login, no response"
date: 2009-12-08
forum: New to Ubuntu
---

### Post by Paddy Landau on 2009-12-08
I installed Karmic 9.10 on a friend's machine a month ago. Everything was working OK (Ubuntu Karmic 9.10).

Since yesterday evening, on booting, he gets the Grub prompt, then the circle, then a blank screen and nothing else.

He can press Ctrl-Alt-Delete to reboot, but the same thing happens every time.

The default kernel shown at the Grub is 2.6.31-16. When he boots with the other alternative, 2.6.31-14, exactly the same thing still happens.

Please help.

---

### Post by Locke_99GS on 2009-12-08
Did he run out of space on his linux partitions? This can cause all sorts of odd breakages. Try switching to tty1 (if it will let you) to log in and update, check for free space, etc...

---

### Post by ukripper on 2009-12-08
Boot into second option from grub menu - recovery mode. Then fix X server by selecting option there from drop down. after recovery has fixed display, reboot normally and se if it has fixed the issue. if not we go from there.

---

### Post by Paddy Landau on 2009-12-08
> **Locke_99GS said:**
> Did he run out of space on his linux partitions? This can cause all sorts of odd breakages. Try switching to tty1 (if it will let you) to log in and update, check for free space, etc...
Thanks for the idea. It's very unlikely (he's not a power user and doesn't download stuff from the 'net), but as you'll see from my next post, we can't even get that far...

---

### Post by Paddy Landau on 2009-12-08
> **ukripper said:**
> Boot into second option from grub menu - recovery mode. Then fix X server by selecting option there from drop down. after recovery has fixed display, reboot normally and se if it has fixed the issue. if not we go from there.
We booted into the Recovery Mode, and got some strange results.

I've attached a photograph of the screen. It's really hard to read, so I've also copied the screen into this post below. It looks like data corruption, from what I can see, but I'm hoping that you can tell me no, it's something more easily fixed.

At the command prompt, the computer did not recognise *sudo*.

More information:

[LIST]
[*]**root** is on **sda6**
[*]**/home** is encrypted and on **sda7** (I do have the 32-character encrypt password, just in case)
[/LIST]
 
Here's what was on the screen:

```
[   19.862211] ata1.00: status: { DRDY ERR }
[   19.864027] ata1.00: error: {UNC }
[   19.888639] ata1.00: configured for UDMA/100
[   19.890440] ata1: EH complete
[   23.900308] ata1.00: exception Emask 0x0 SAct 0x0 Serr 0x0 action 0x0
[   23.902105] ata1.00: BMDMA stat 0x25
[   23.903874] ata1.00: cmd c8/00:00:3e:da:2a/00:00:00:00:00/e5 tag 0 dma 131072 in
[   23.903875]          res 51/40:00:3e:da:2a/00:00:00:00:00/e5 Emask 0x9 (media error)
[   23.907503] ata1.00: status: { DRDY ERR }
[   23.909327] ata1.00: error { UNC }
[   23.932655] ata1.00: configured for UDMA/100
[   23.934421] ata1: EH complete
[   27.934162] ata1.00: exception Emask 0x0 SAct 0x0 Serr 0x0 action 0x0
[   27.935959] ata1.00: BMDMA stat 0x25
[   27.937775] ata1.00: cmd c8/00:00:3e:da:2a/00:00:00:00:00/e5 tag 0 dma 131072 in
[   27.937776]          res 51/40:00:3e:da:2a/00:00:00:00:00/e5 Emask 0x9 (media error)
[   27.941483] ata1.00: status: { DRDY ERR }
[   27.943319] ata1.00: error { UNC }
[   27.968655] ata1.00: configured for UDMA/100
[   27.970458] sd 0:0:0:0: [sda] Unhandled sense code
[   27.972283] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   27.974103] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[   27.975912] Descriptor sense data with sense descriptors (in hex):
[   27.977736          72 03 11 01 00 00 00 0c 00 0a 80 00 00 00 00 00
[   27.979629]         05 2a da 3e
[   27.981451] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[   27.983285] end_request: I/O error, dev sda, sector 86694462
[   27.985165] ata1: EH complete
[   27.987041] JBD: Failed to read block at offset 152
[   27.988926] JBD: recovery failed
[   27.990755] EXT4-fs (sda6): error loading journal
mount: mounting /dev/disk/by-uuid/0a55f2801-059f-40d9-bd32-f78aded762fe on /root failed: invalid argument
Begin: Running /scripts/local-bottom ...
Done.
Done.
Begin: Running /scripts/init-bottom ...
Begin: Starting AppArmor profiles ...
mount: mounting /sys on /root/sys failed: No such file or directory
mount: mounting /dev on /root/dev failed: No such file or directory
Done.
mount: mounting /sys on /root/sys failed: No such file or directory
mount: mounting /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have /bin/init.
No init found. Try passing init=bootarg.


BusyBox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu7) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)
```

---

### Post by ukripper on 2009-12-08
> mount: mounting /dev/disk/by-uuid/0a55f2801-059f-40d9-bd32-f78aded762fe on /root failed: invalid argument


Looks like your fstab mount points are not detected by init. Can you go into BIOS and check if your Hardrive is showing up there. I suspect your HDD might be playing up. Check BIOS if it shows there.

---

### Post by Paddy Landau on 2009-12-08
> **ukripper said:**
> Looks like your fstab mount points are not detected by init. Can you go into BIOS and check if your Hardrive is showing up there. I suspect your HDD might be playing up. Check BIOS if it shows there.
The BIOS does show the hard drive. I expected it to, because the computer does get as far as the Grub and starting to load Linux, which means that the drive is visible.

(There is only one drive, split into partitions: sda1 = Windows XP, sda5 = Linux swap, sda6 = Karmic root, sda7 = /home.)

I checked something else: The computer boots Windows XP without any problem.

So, it seems to me that the Ubuntu partition sda6 is doing something funny.

You may be right that the drive is playing up; how can I test this?

I may have to back up the data onto an external drive using Live CD, and reinstall Karmic.

... Unless you have any bright ideas!

Thanks for your help so far.

---

### Post by ukripper on 2009-12-08
> The BIOS does show the hard drive. I expected it to, because the computer does get as far as the Grub and starting to load Linux, which means that the drive is visible.


I was thinking you had two drives, first one has grub installed and second got root and having problems. 

Nevermind back to the problem. Boot into the live cd and post output of this command:
```
sudo blkid
```

Need to make sure UUID is correct for your root

---

### Post by Paddy Landau on 2009-12-09
Thanks for all the help.

We've found out the problem.

The hard drive developed bad sectors and it KO'd the root partition.

---

