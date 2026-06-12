---
title: "Did stupid witirh multiboot"
date: 2009-08-08
forum: New to Ubuntu
---

### Post by Paul-RT on 2009-08-08
Hello. I'm new to this forum, but double moderator on a dutch pc help forum.
First of all, sorry for bad english. I'm Dutch.....

What happened:
I do have only 0.5 % knowledge of Kubuntu or other linux.
I do have a nice desktop, with a muiltiboot: Xp prof (C:\) Vista (D:\) and Kubuntu ( " E:\ " )
It did work perfect. Booted, asked which system i like to start this time. 100% ok.

The last one allways gives trouble in windows.
Sometimes kubuntu partitions shows as a cd-rom player to windows, sometimes as a E:\ partition.
It just can't handle correct.

Now last time i did ad a 1 Tb harddisk to my existing 1,5 Tb.
I like to split the 1 Tb in 2 parts. A partition I:\ and a part J:\
But, this time, the linux shows as cd-rom player J:\.

I have had it with kubuntu so far, as i never use it.
I decided to kill the linux partitions, using harddisk management in windows xp.

Rebooted the computer  and it stops at:
> GRUB Loading stage 1.5
Grub loading, please wait
Error line 22That's all.

For this time i don't have the setup cd-rom available, but able to use another desktop and download it. Probably no iso creation program there.

What to do, to skip the boot of linux, or restore what i did wrong ?!
Any solutions?
Possible to edit the linux bootloader?
I do have an option to swap the harddisk into a bracked of another desktop, to be able to edit the files.

Please answers in easy english ;)

---

### Post by benerivo on 2009-08-08
I would use [Super Grub Disk ]("http://www.supergrubdisk.org/")to restore the Windows mbr bootloader.

---

### Post by Paul-RT on 2009-08-08
Ok, downloaded...
Will use my wife's desktop to burn a cd-rom by tomorrow.
(passed midknight right now)

I'll reply what happened.

Thanx so far, Benerivo.

[COLOR=Gray]( hmmm, that " first cup of ubuntu" isn't so bad..... )[/COLOR]

---

### Post by presence1960 on 2009-08-08
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Boot your XP install disk and follow the instructions for XP on that link. if you only have a recovery CD or recovery partition you may have to use super grub disk.

The reason you have to do one or the other is when you installed Kubuntu GRUB overwrote the windows bootloader on your MBR. All you need to do is restore windows bootloader to MBR.

---

### Post by stlsaint on 2009-08-08
considering that you erased the ubuntu partitions than prolly want to use the recover cd for xp!! cuz like presence said Grub overwrites MBR when its installed.

---

### Post by Paul-RT on 2009-08-09
@benerivo:
Burned the iso on cd-rom, and booted on it.
The program comes, and whatever i do, it comes with an error.
So i tried to boot on XP setup cd-rom.

@ Presence1960:
fixboot doen's exist.
fixmbr came with a warning that i might lose all my files.
Whatever. Last backup is 6 month old. Won't be too bad.
It did workout.
XP or vista running again.

Now i'll have to fix my drive-letters, and then i'll be back.
Trying to get ubuntu 9.something up and running again.
100Gb partiton rerady for a 3-splt.

@Stlsaint: Thanx anyway :)

Thanx for now, i'll be back :) ):P

---

