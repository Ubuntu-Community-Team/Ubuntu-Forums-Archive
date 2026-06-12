---
title: "Completely remove ubuntu 8.10 and 7.10 from my laptop"
date: 2009-01-17
forum: New to Ubuntu
---

### Post by Austin_Duffy on 2009-01-17
Yeah, unfortunately I found out that i prefer Slackware 12.2 better for my Linux distro. 

So if possible someone instruct or link me how to remove it from grub menu so I can have some memory.

---

### Post by seagullplayer77 on 2009-01-17
Do you already have Slackware installed on your laptop? If not, I think it would just be as simple as formatting your whole drive and installing Slackware over the free space.

If you've already got Slackware installed, then I suppose you could try using a utility like Gparted or a UBCD to format your Ubuntu partitions. Then, you could use the formatted partitions as space for your Slackware install. 

Before you go around formatting things, though, I'd try getting an opinion from someone more experienced with Linux than myself.

---

### Post by 73ckn797 on 2009-01-17
If you do not have Slackware installed and are not dual booting, then you can use the Ubuntu Live CD to re-format the drive and then install Slackware fresh. Slackware may also take care of all of this itself.

To edit the grub you may need to boot from the Ubuntu Live CD and edit grub via terninal from the CD. It could be accessed via terminal as ```
gksudo gedit /media/disk-?/boot/grub/menu.lst
```The "?" would designate the drive where "menu.lst" resides. That can be found using Places/Computer.

Your Live CD Computer location might show something similar to:
```
/media/disk-1/boot/grub
```You would then, via terminal on Live CD, enter:
```
gksudo gedit /media/disk-1/boot/grub/menu.lst
```[SIZE=1]*(The "Disk-1" may be different than your setup.}*[/SIZE]

And make the necessary edits to boot from.

I would also assume that if you install Slackware to the entire drive you can just let the installation over-write the entire drive and things would take care on it's own.

---

