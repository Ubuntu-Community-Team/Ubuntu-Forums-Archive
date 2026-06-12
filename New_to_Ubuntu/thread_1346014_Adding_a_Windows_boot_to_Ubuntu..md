---
title: "Adding a Windows boot to Ubuntu."
date: 2009-12-04
forum: New to Ubuntu
---

### Post by Kraust on 2009-12-04
I want to Dual Boot Ubuntu Lucid (currently installed) and a Windows OS (Probably 2K due to it's small size).

I only have 1 Hard Drive. Can I resize my current Partition and Install the Windows OS? I only need around 3 GB for the install as I'm only going to be playing games and those games (old games) and those games will be saved on a removable media. 

And would I need to use Microsoft's Bootloader? Or can I use Grub to do this? My Grub version is pretty old as this format is from an old Intrepid install.

Also, my Grub version is probably pretty old as well. The output of Grub --version says that it's 0.97. I know that there's at least Grub 2 so yea. Old.

And for that matter, my only Partition (excluding my Swap) is in ext3 and not ext4.

And no, I can't use Wine to play this game, because of my bad System Specs.

---

### Post by ed-koala on 2009-12-04
I'm no expert on this, but one thing I do know ... when you install Windows it is gonna screw your boot for Ubuntu.  Windows will write its own MBR and won't care about grub, so you'll have to do some extra work after to get Ubuntu booting again.

There are threads here telling how to do this.  I just know from my reading it's easier to install Windows first, then Ubuntu rather than the other way around.

---

### Post by Shibblet on 2009-12-04
> **Kraust said:**
> And would I need to use Microsoft's Bootloader? Or can I use Grub to do this? My Grub version is pretty old as this format is from an old Intrepid install.

I usually have to install Windows first, then Ubuntu second.  That way Grub knows where to go to boot from Windows.

And off subject... Is that a Lloyd Irving / Tux icon?

---

### Post by Kraust on 2009-12-04
Yes that's Lloyd <_<.

Also, I really don't want to lose my current Ubuntu install. Everything has been going very well so far and such. I've fixed *most* of the problems I've had that would take days to fix.

---

### Post by ed-koala on 2009-12-04
Oh, you won't "lose" your install, you'll just have to re-do grub before it'll boot up.  Just research it a bit to see how it's done first.

---

### Post by Merk42 on 2009-12-04
What specific games are you trying to run that'll have you install an out of date operating system that's no longer supported?

WINE working or not has nothing to do with "bad System Specs". Though I am intrigued as to what those are too.

---

### Post by Kraust on 2009-12-04
> **Merk42 said:**
> What specific games are you trying to run that'll have you install an out of date operating system that's no longer supported?

WINE working or not has nothing to do with "bad System Specs". Though I am intrigued as to what those are too.

It has a lot to do with my Ancient CPU, and not my Graphics, Ram or anything else (which are all fine).

Old CPUs have a harder time running stuff in general. And Wine in itself is a very resource intensive program to my knowledge (with some things).

And I found out what I have to do. Thank you for your help.

---

### Post by Merk42 on 2009-12-04
> **Kraust said:**
> It has a lot to do with my Ancient CPU, and not my Graphics, Ram or anything else (which are all fine).

Old CPUs have a harder time running stuff in general. And Wine in itself is a very resource intensive program to my knowledge (with some things).

And I found out what I have to do. Thank you for your help.

Well WINE isn't any more resource intensive than native, in fact in some cases it's actually LESS intesive.

While you can do a dual boot, I just figured WINE and/or Virtualbox would be a MUCH easier thing to set up.

---

### Post by oldfred on 2009-12-04
How to recover boot loaders:

restore boot loaders Ubuntu Win xp Vista
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

