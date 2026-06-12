---
title: "Ubuntu / XP - Grub menu?"
date: 2009-02-13
forum: New to Ubuntu
---

### Post by Stalker72 on 2009-02-13
I installed XP after Ubuntu. When the PC boots up, I don't see a menu where I can choose between those two operating systems. What should I do?

Stalker72

---

### Post by 2hot6ft2 on 2009-02-13
Since you don't give any system info like if there's more than one drive.
Sounds like you just need to restore Grub to your MBR, so if you boot your Live CD, open a terminal (Applications > Accessories > Terminal) and do:

```
sudo grub
grub> root (hd0,0)
grub> setup (hd0)
grub> quit
```

And that's all it should take.

If there is more than one drive then use these instead
```
sudo grub
find /boot/grub/stage1

```
This will return (hdX,Y), where X and Y are some numbers. Use these numbers below:

```
root (hdX,Y)
setup (hdX)
quit
```

---

### Post by Stalker72 on 2009-02-13
I have one HDD.

My partitions are as follows:

500 GB /home - XFS
15 GB /root - JFS
6 GV /var - ReiserFS
1 GB swap
About 450 GB XP - NTFS

Stalker72

---

### Post by 2hot6ft2 on 2009-02-13
Then use either set of commands in a terminal while using the livecd and it should fix it right up.

I would go ahead and use the second set so it will know where the menu.lst file is but either should work.

---

### Post by kansasnoob on 2009-02-13
Nothing wrong with the instructions given but maybe simplifying would be helpful.

Boot any Ubuntu Live CD, just choose to "Run without changes.......", and then from the "Live Desktop" go to  Applications > Accessories > Terminal. In terminal either type or copy-n-paste this command:

```
sudo grub
```

That will result in this:

>  [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]

grub> 


So the rest of these commands will be done in "GRUB mode". So next enter the command:

```
find /boot/grub/stage1
```

That will return an output something like:

> (hd0,0)

Those are zeros! The first zero means drive #1, the second zero means partition #1 - because GRUB begins numbering with 0 (zero)!

Anyway whatever that output shows you need to use with the next command to set "root":

```
root (hd0,0)
```

The next command concerns only the drive # so you drop the last ",0" or whatever digit it is so the next command would be:

```
setup (hd0)
```

Then simply follow that by running the command:

```
quit
```

Which drops you back to a normal terminal prompt like:

> lance@lance-desktop:~$ sudo grub
[sudo] password for lance: 
Probing devices to guess BIOS drives. This may take a long time.
lance@lance-desktop:~$ 


Oh, and then of course you restart, remove the Live CD and hopefully you're dual booting!

---

### Post by Stalker72 on 2009-02-27
Grub is OK now, but XP doesn't show up! :confused:

Stalker72

---

### Post by thtrgremlin on 2009-02-27
The entries for grub are in /boot/grub/menu.lst

From the documentation in that file:
> # examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro

If you add those 4 lines to the end of your menu.lst file, it will let you boot to windows, assuming windows is installed on sda1 (a = first disk, 1 = first partition)

If you are not sure, use ```
fdisk -l
``` and look for the entry where it has a '*' under 'boot' and formatted 'ntfs'. For example, if it says /dev/sda2 is formatted ntfs, then that is probably windows and where it says "root (hd0,0)" would become "root (hd0,1)".

Oh, and in case it needed to be said, when you add the entries, they do not begin with '#', that 'comments them out' so they are not active.

Hope that helps.

If you are not sure, post your /boot/grub/menu.lst and the output of 'fdisk -l'

Good luck

---

### Post by Stalker72 on 2009-03-01
Solved! :)

Stalker72

---

