---
title: "Grub rescue"
date: 2010-07-11
forum: New to Ubuntu
---

### Post by Kirkland14 on 2010-07-11
so I was trying to dual boot Ubuntu with win XP.  Ubuntu was having a problem loading from the HDD so i used gparted to uninstall it(which I 've done before.  apparently I somehow nuked winxp as well or something and all I get now(even when I tried to use the reinstall XP disk) is GRUB RESCUE.  Im pretty new to this so laymens terms would be nice. Thanks

Kevin

ps  apparently I didnt nuke winxp but it just won't find it when it loads.

---

### Post by lindsay7 on 2010-07-12
you should find what you need here.  I would start with the xp section on fixboot

[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by oldfred on 2010-07-12
If you removed Ubuntu the grub in the MBR cannot find the rest of the boot.

Description of the Windows XP Recovery Console for advanced users
[http://support.microsoft.com/kb/314058/](http://support.microsoft.com/kb/314058/)
To run the Recovery Console from the Windows XP startup disks or the Windows XP CD-ROM, follow these steps:
1.    Insert the Windows XP startup disk into the floppy disk drive, or insert the Windows XP CD-ROM into the CD-ROM drive, and then restart the computer.

Click to select any options that are required to start the computer from the CD-ROM drive if you are prompted.
2.    When the "Welcome to Setup" screen appears, press R to start the Recovery Console.
3.    If you have a dual-boot or multiple-boot computer, select the installation that you must access from the Recovery Console.
4.    When you are prompted, type the Administrator password. If the administrator password is blank, just press ENTER.
5.    At the command prompt, type this commands one at a time.

FIXMBR  C:
FIXBOOT  C:

---

### Post by Kirkland14 on 2010-07-12
when I install the xp cd and go to boot from cd it says

```
Press any key to boot from CD.....
```

when i press any key I get

```
grub rescue>
```

I'm lost

---

### Post by oldfred on 2010-07-12
You did not press the 'any' key..... sorry reverse of old joke:smile:

It looks like the CD is not booting as if that is coming up it is from the Hard Drive. Double check CD and CD Drive and BIOS settings.

---

### Post by lindsay7 on 2010-07-12
startup you computer and get into the bios.  Hit the Del key when starting or the f2 key or f12 key on some computers.  Make sure the bios start up order is cd/dvd first and then hd second. Make sure that the hd you chose is the one where the os is located.

---

### Post by Kirkland14 on 2010-07-12
> **lindsay7 said:**
> startup you computer and get into the bios.  Hit the Del key when starting or the f2 key or f12 key on some computers.  Make sure the bios start up order is cd/dvd first and then hd second. Make sure that the hd you chose is the one where the os is located.

I hit esc to go to boot and manually choose cd/dvd  when prompted I hit "any"(HAHA) key and that's when grub rescue came up

---

### Post by lidex on 2010-07-12
Well it's not booting from the disk, so something is not right with that sequence of events. Maybe you weren't quick enough. That is a bootable disk, correct?

---

### Post by Kirkland14 on 2010-07-12
it is  the XP installation disk


AAAHHHH!!!! fast enough!!!! thanks!!!!

---

### Post by Kirkland14 on 2010-07-12
> **oldfred said:**
> If you removed Ubuntu the grub in the MBR cannot  find the rest of the boot.

Description of the Windows XP Recovery Console for advanced users
[http://support.microsoft.com/kb/314058/](http://support.microsoft.com/kb/314058/)
To run the Recovery Console from the Windows XP startup disks or the  Windows XP CD-ROM, follow these steps:
1.    Insert the Windows XP startup disk into the floppy disk drive, or  insert the Windows XP CD-ROM into the CD-ROM drive, and then restart the  computer.

Click to select any options that are required to start the computer from  the CD-ROM drive if you are prompted.
2.    When the "Welcome to Setup" screen appears, press R to start the  Recovery Console.
3.    If you have a dual-boot or multiple-boot computer, select the  installation that you must access from the Recovery Console.
4.    When you are prompted, type the Administrator password. If the  administrator password is blank, just press ENTER.
5.    At the command prompt, type this commands one at a time.

FIXMBR  C:
FIXBOOT  C:

so I did this and it said a new bootloader was installed.  When I tried  to start up again I got the same thing:

```
error: unknown filestystem.
grub rescue>
```Thanks for your help

Kevin

---

### Post by Kirkland14 on 2010-07-12
> **lindsay7 said:**
> you should find what you need here.  I would start with the xp section on fixboot

[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

THANKS ALOT!!!  I got it all working back to normal.  Thanks for everyones help

Kevin

---

### Post by lindsay7 on 2010-07-12
Congrats, good for you!

---

### Post by Kirkland14 on 2010-07-12
thanks.  I've really only been messing around with computers about 6 months now.  I totally thought I screwed myself

---

