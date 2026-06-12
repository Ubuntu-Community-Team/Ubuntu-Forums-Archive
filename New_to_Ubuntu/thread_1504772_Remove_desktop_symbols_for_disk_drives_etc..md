---
title: "Remove desktop symbols for disk drives etc.?"
date: 2010-06-08
forum: New to Ubuntu
---

### Post by ManfredKlinglmair on 2010-06-08
Hi,
one thing that really annoys me about my desktop (Ubuntu 10.4), even though it's a small issue, is the fact that my disk drives (HDD partitions, and the microSD card in my 3G modem) are always shown on my desktop, and I cannot figure out how to remove them just like other desktops shortcuts and such.

I'd like my desktop as uncluttered as possible, so I would be happy to remove these symbols. Ideas?

Manfred

---

### Post by Philip Gray on 2010-06-08
Hi select Alt+F2 then enter gconf-editor. Then go down to apps/nautilus/desktop and deselect the check box next to 'volumes_visible'. Not sure how to remove the 3G icon. I have the same issue with my vodafone modem.

Regards
Philip

---

### Post by irv on 2010-06-08
As far as the HD go, all you have to do is unmount them. Just right mouse click and unmount. As far as the 3g goes I am not sure because I do not have a 3g. After unmounting the drives they will still be under the "Place" menu and when you select them they will remount. I am like you I keep a clean desktop.
[ATTACH]159754[/ATTACH]

---

### Post by indytim on 2010-06-08
I agree, it's a real annoyance.  It's one of those Gnome thingers (at least with respect to Ubuntu and derivatives).  I think the desktop gets happy with anything that is mounted in /media.  I have 17 partitions that I mount on bootup through fstab.  My end point solution is to mount all of my internal hd partitions in /mnt vs the convenient /media.  You'll still be stuck with the removable devices, but moving to /mnt should clear the desktop abit.

IndyTim / DataMan

---

### Post by Philip Gray on 2010-06-08
Hi indytim I use NTFS Config to mount my Windows XP partitions. Is fstab a better program to use?

Regards
Philip

---

### Post by fotoflojoe on 2010-06-08
Ding, Ding, Ding!
**Philip Gray** is the winner!

Follow instructions in post #2.

I struggled with this too for a bit. Settings in gconf-editor did the trick!

---

### Post by ManfredKlinglmair on 2010-06-08
Yes! Thanks Philip Gray!
M.

---

### Post by ScottinSoCal on 2010-06-08
> **Philip Gray said:**
> Hi indytim I use NTFS Config to mount my Windows XP partitions. Is fstab a better program to use?

fstab is a file that runs to auto-mount partitions. I use it to mount network partitions on bootup for my work computer, and to mount a second hard drive in a non-standard location on my personal computer.

---

### Post by formaldehyde_spoon on 2010-06-08
Anything mounted inside /media will be visible on the desktop.
Mount in /mnt (or somewhere else) to avoid this.

---

### Post by karthick87 on 2010-06-08
> **formaldehyde_spoon said:**
> Anything mounted inside /media will be visible on the desktop.
Mount in /mnt (or somewhere else) to avoid this.


By default it will mount in /media ,can you say me how to change the mount location so that i can mount my drives to /mnt

---

### Post by formaldehyde_spoon on 2010-06-11
> **getyourkarthick said:**
> By default it will mount in /media ,can you say me how to change the mount location so that i can mount my drives to /mnt

1. Create a target directory in /mnt: sudo mkdir /mnt/myTarget

 2. Edit ftsb: sudo gedit /etc/fstab

 3: Change one instance of ''/mnt/xxx'' (where xxx is sda1 or similar) to ''/mnt/myTarget''

---

