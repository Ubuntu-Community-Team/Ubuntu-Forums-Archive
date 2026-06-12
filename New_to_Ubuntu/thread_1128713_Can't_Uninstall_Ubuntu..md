---
title: "Can't Uninstall Ubuntu."
date: 2009-04-17
forum: New to Ubuntu
---

### Post by SLaCK3r on 2009-04-17
Hi. I want to un-install Ubuntu and replace it with Windows Vista because I can't do the things that I like to do on Ubuntu. When I get to Vista's partition part with the boot from disk, it says that I have 120 something GB on that drive, but 0 MB free. Same with the other. I can't format either drive and I don't know how to delete Ubuntu. I installed Ubuntu 8.10 from a disk. Please help.

Sincerely, 

Dan.

---

### Post by skymera on 2009-04-17
This isn't really an Ubuntu problem :)

If the Vista disc cannot format your hard disk, that's a Vista problem.

Anyway try booting Ubuntu LiveCD and use gParted to format. Then try Vista.

---

### Post by swoll1980 on 2009-04-17
You can delete the partitions from the vista installer, or from a Linux partitioning tool, like gparted. IT can't be uninstalled only deleted.

---

### Post by James_Lochhead on 2009-04-17
[LIST]
[*]Grab a Live CD (i.e. a "normal" Ubuntu CD".
[*]Drop in the the CD drive.
[*]Reboot your computer and change the boot order to boot the CD first (in your BIOS).
[*]Let the computer boot from the CD.
[*]When a menu pops up pick try Ubuntu after picking your language.
[*]When Ubuntu is loaded press alt+f2, type gksudo gparted and press enter.
[*]Delete all the Linux partitions (most likely ext3).
[*]Apply the changes.
[*]Reboot the computer.
[*]You should now be able to install Vista.
[/LIST]

---

### Post by presence1960 on 2009-04-17
> **SLaCK3r said:**
> Hi. I want to un-install Ubuntu and replace it with Windows Vista because I can't do the things that I like to do on Ubuntu. When I get to Vista's partition part with the boot from disk, it says that I have 120 something GB on that drive, but 0 MB free. Same with the other. I can't format either drive and I don't know how to delete Ubuntu. I installed Ubuntu 8.10 from a disk. Please help.

Sincerely, 

Dan.

Boot from the Ubuntu live CD, use gparted (partition editor) and delete the Ubuntu partition(s). Format the unallocated space to NTFS. Close gparted and reboot. Now use your Vista DVD.

I would recommend a dual boot setup for you, but someone convinced against their will is not really "convinced" Good luck with Windows, there is no shame in using Windows. But if you ever get tired of re-experiencing the reason(s) you tried Ubuntu in the first place remember Ubuntu and this forum.

---

### Post by SLaCK3r on 2009-04-17
Thank you everyone. It's not that I don't like Ubuntu, it's just that I can't play games and stuff on it. It's not quite "perfected" yet, if you know what I mean. Vista, by no means, is perfected either.

---

### Post by presence1960 on 2009-04-17
> **SLaCK3r said:**
> Thank you everyone. It's not that I don't like Ubuntu, it's just that I can't play games and stuff on it. It's not quite "perfected" yet, if you know what I mean. Vista, by no means, is perfected either.

If games are what you want, consider dual boot set up with Vista/Ubuntu. You can choose which OS you want to boot into at startup. I dual boot because my job doesn't want me using Open Office for work, something to do with formatting not 100% the same between open Office and MS Office. So I use XP for MS Office and Acrobat Professional.

It's not that Ubuntu isn't perfected, it's the fact that the games manufacturers don't make a linux version.

---

### Post by SLaCK3r on 2009-04-17
I have a problem. I boot from the CD and press right ALT + F2 and nothing happens. I Google'd "gparted" and it came up with the Gnome program. Should I use that?

---

### Post by James_Lochhead on 2009-04-17
You already have it. That was just the command to open it. You might be able to find it in System > Administration > Partition Editor. Or you can open a terminal, type sudo gparted and press enter.

---

### Post by presence1960 on 2009-04-17
> **SLaCK3r said:**
> I have a problem. I boot from the CD and press right ALT + F2 and nothing happens. I Google'd "gparted" and it came up with the Gnome program. Should I use that?

Boot Live CD, choose use without any changes to your computer. When desktop appears go Applications > Accessories > Terminal. In terminal enter ```
gksu gparted 
``` This will open gparted for you.

---

### Post by James_Lochhead on 2009-04-17
By the way, are you sure that you are pressing the right combo?

alt + f2 means hold alt then press f2. And it must be left alt, right alt does not work for me either.

---

### Post by SLaCK3r on 2009-04-17
> **James_Lochhead said:**
> By the way, are you sure that you are pressing the right combo?

alt + f2 means hold alt then press f2. And it must be left alt, right alt does not work for me either.

I don't know if this matters, but I downloaded the ISO on my Windows and then burned it to a CD. Does that matter?

---

### Post by presence1960 on 2009-04-17
> **SLaCK3r said:**
> I don't know if this matters, but I downloaded the ISO on my Windows and then burned it to a CD. Does that matter?

shouldn't matter. boot the CD and choose check CD for defects. If it is ok choose try ubuntu without any changes. when desktop loads use the instructions provided earlier to open gparted and take care of your partition(s) .

---

### Post by aldrinmirambel on 2009-04-17
Have you try installing Vista without deleting the Ubuntu?
Try it. It's still ok if you have dual OS, but if it doesn't still work, I think it's Ubuntu's problem. You cannot install other OS while he's running.

__________________________
[Art Framed, Posters, Art Prints](http://www.ichatart.com/)

---

### Post by barney385 on 2009-04-17
> **SLaCK3r said:**
> Thank you everyone. It's not that I don't like Ubuntu, it's just that I can't play games and stuff on it. It's not quite "perfected" yet, if you know what I mean. Vista, by no means, is perfected either.

I dual-boot with XP just for this reason(Games).

I know better than to let MS anything anywhere near the interweb...


If you surf the interweb, I would seriously reconsider your decision to dump Ubuntu...


Good Luck

---

### Post by jbaerbock on 2009-04-18
Gaming has always been my hangup with Linux as well. But now that I signed up with Cedega I install things as easily as in Windows so you may wanna give that a try if you want to commit to Linux.

---

