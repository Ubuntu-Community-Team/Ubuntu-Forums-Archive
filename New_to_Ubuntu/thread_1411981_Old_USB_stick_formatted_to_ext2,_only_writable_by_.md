---
title: "Old USB stick formatted to ext2, only writable by root"
date: 2010-02-20
forum: New to Ubuntu
---

### Post by karatedog on 2010-02-20
I found an old USB stick (Kingston 512 Mb, USB 1.1 version) in my drawer and just got the idea to install Damn Small Linux on it. Not knowing what file system it would need, I deleted all partition from the stick, created a new ext2 and formatted it.
Being newbie, I let the automount feature to work.

The stick is mounted this way:

[FONT="Courier New"]/dev/sdb1 on /media/kingston512 type ext2 (rw,nosuid,nodev,uhelper=devkit)[/FONT]

Problem: I cannot write to the stick with normal user only with root user.

So I deleted again all partition, and created a new, now fat32.
Mounting is now different:

[FONT="Courier New"]/dev/sdb1 on /media/kingston512 type vfat (rw,nosuid,nodev,uhelper=devkit,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)[/FONT]

And the write problems are gone.

I haven't tried to manually mount the ext2 partition with my own parameters, but why these 2 behave differently?

---

### Post by cariboo on 2010-02-20
Vfat doesn't use permissions of any sort. Have you tried letting the thumbdrive automount?

---

### Post by karatedog on 2010-02-21
> **cariboo907 said:**
> Vfat doesn't use permissions of any sort. Have you tried letting the thumbdrive automount?

Yes, I let it automount.

---

### Post by Morbius1 on 2010-02-21
External drives by default automount differently depending on how they're formatted. One formatted in ext3/4 will be treated as an extension of the base root file structure.  To resolve your problem with ext2/3/4 USB devices:
[B][FONT=Courier New]
sudo chmod -R 0777 [/FONT][/B][B][FONT=Courier New]/media/kingston512

[/FONT][/B][FONT=Courier New]This will have owner = root but allow everyone to have access.[/FONT][B][FONT=Courier New]




[/FONT][/B]

---

### Post by karatedog on 2010-02-21
> **Morbius1 said:**
> External drives by default automount differently depending on how they're formatted. One formatted in ext3/4 will be treated as an extension of the base root file structure.  To resolve your problem with ext2/3/4 USB devices:
[B][FONT=Courier New]
sudo chmod -R 0777 [/FONT][/B][B][FONT=Courier New]/media/kingston512

[/FONT][/B][FONT=Courier New]This will have owner = root but allow everyone to have access.[/FONT][B][FONT=Courier New]
[/FONT][/B]

Worked! Thanks!

---

