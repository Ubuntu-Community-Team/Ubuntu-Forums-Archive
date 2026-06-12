---
title: "Booting to XP via GRUB :-("
date: 2009-01-25
forum: New to Ubuntu
---

### Post by Alexmouse on 2009-01-25
I've a newbie who's installed Ubuntu (very impressed), and is now trying to re-establish access to my Windows XP, I boot via GRUB.
My disc is partitioned thus:

[I]/dev/hda1 ext3 Linux partition
/dev/hda2 Linux swap disc
/dev/hda3 NTFS Windows XP installation
/dev/hda4 FAT32 Shared disc[/I]

The GRUB menu boots Ubuntu fine, but my attempts to boot to XP either give messages about non-bootable discs or Error 23 while parsing.

Any ideas?


An extract of menu.lst:

[I]## ## End Default Options ##

title		Ubuntu 7.10, kernel 2.6.22-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-16-generic root=UUID=c6cc2e68-5688-4e43-aeb4-34575c4026a3 ro quiet splash
initrd		/boot/initrd.img-2.6.22-16-generic
quiet

title		Windows XP
map (hdo) (hd2)
map (hd2) (hd0)
rootnoverify	(hd2,0)
makeactive
chainloader	+1[/I]

---

### Post by billgoldberg on 2009-01-25
Try this instead of the windows entry you got in the grub now:

title Windows
root (hd0,2)
chainloader +1

--

Could be 

root (hd2,0) 

I get confused sometimes :p

Also Ubuntu 7.10 is an old release, I would advice you install Ubuntu 8.10 instead.

---

### Post by Elfy on 2009-01-25
Try

```
title  Windows XP
rootnoverify (hd0,2)
makeactive
chainloader  +1
```

Backup the file before you edit it

```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.2501
gksudo gedit /boot/grub/menu.lst
```

---

### Post by kestrel1 on 2009-01-25
My menu.lst file looks like this for Windows:
```
title        Microsoft Windows XP Professional
root        (hd0,0)
savedefault
makeactive
chainloader    +1
```
Looking at your setup I would say this should work```
title        Microsoft Windows XP
root        (hd2,0)
savedefault
makeactive
chainloader    +1
```

---

### Post by leonardo_neo on 2009-01-25
You can try Super Grub Disk to fix the problem. Download iso image of Super Grub Disk from the following link

> [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

### Post by Alexmouse on 2009-01-25
Thanks for your help guys, that did the trick, I'm back in Windoze again. I was almost there but 'almost' isn't good enough in computing - and once I've learned a bit more I might understand where I went wrong and how I fixed it.

---

### Post by kestrel1 on 2009-01-25
For reference, What did the trick?

---

### Post by Alexmouse on 2009-01-25
Here it is, very simple when you know how, aching brain & frustration when you don't.

[I]title        Microsoft Windows XP
root        (hd0,2)
savedefault
makeactive
chainloader    +1[/I]

---

### Post by Elfy on 2009-01-25
Originally you had
rootnoverify (hd2,0)

what worked was
root (hd0,2)

The changes you made were quite big - although it mightn't seem so :)

The way grub works is that the first hdd is 0 and the first partition is also 0 

So you were telling grub that xp was on the third harddrive and on it's first partition, what you really needed was the first harddrive and third partition.

[http://users.bigpond.net.au/hermanzone/p15.htm#A_Quick_Guide_to_Grubs_Numbering_System](http://users.bigpond.net.au/hermanzone/p15.htm#A_Quick_Guide_to_Grubs_Numbering_System)

---

### Post by Alexmouse on 2009-01-30
I switched the machine on today and menu.lst was back to defaults, my XP option was gone! Is this Ubuntu being defensive? ;)
Fortunately I'd backed my changes.
Any idea how this might have happened?

---

### Post by adrian15 on 2009-03-18
> **Alexmouse said:**
> I switched the machine on today and menu.lst was back to defaults, my XP option was gone! Is this Ubuntu being defensive? ;)
Fortunately I'd backed my changes.
Any idea how this might have happened?

Please update groot variable in menu.lst and run update-grub to check that your change has taken into account.

Why don't you advice to newbie people to edit what-I-call-update-grub-variables ?!!!

adrian15

---

