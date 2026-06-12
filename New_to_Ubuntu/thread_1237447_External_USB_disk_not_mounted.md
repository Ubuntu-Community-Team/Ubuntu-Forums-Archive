---
title: "External USB disk not mounted"
date: 2009-08-11
forum: New to Ubuntu
---

### Post by Nethar on 2009-08-11
Hi, I would like to ask for some help. I am very beginner user of Ubuntu, just few days. I used my USB external Seagate FreeAgent disk - every time it was autodetected by Ubuntu and I could use it. But from yesterday it is not. When I plug it in it switches on, but it is not mounted by Ubuntu (everytime before the icon for it appeared on desktop). The same disk is working on Windows XP on another machine.
I searched for some help but i was not successfull.
Maybe this will help somehow:
```
:~$ lsusb
Bus 001 Device 004: ID 0bc2:3000 Seagate RSS LLC 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 413c:3012 Dell Computer Corp. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```
```
~$ sudo fdisk -l

Disk /dev/sda: 60,0 GB, 60 011 642 880 bajt&#367;
hlav: 255, sektor&#367; na stopu: 63, cylindr&#367;: 7 296
Jednotky = cylindry po 16065 * 512 = 8 225 280 bajtech
Identifikátor disku:&#8239;0xde53de53

Za&#345;ízení Zavád&#283;t   Za&#269;átek       Konec    Bloky    Id  Systém
/dev/sda1   *           1        7134    57303823+  83  Linux
/dev/sda2            7135        7296     1301265    5  Rozší&#345;ený
/dev/sda5            7135        7296     1301233+  82  Linux swap/Solaris

```

So I think it is not even in the list of disks displayed by fdisk. Thanks for help. And sorry for my beginner question ;-)

---

### Post by Buuntu on 2009-08-11
Is it showing up in Computer? If it is all you have to do is right click > mount.
It should show up on the desktop then.
 
If you want it to automount you will have to edit your fstab file.
See if this link helps [http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

---

### Post by Nethar on 2009-08-11
Thanks for answer.

No, it is not showing in Places -> Computer. If I remember it right, it was also in /media folder when it was working automatically, now there is also nothing.

---

### Post by Nethar on 2009-08-17
Any idea please? My disk is still not working :cry:

---

### Post by Cheezespread on 2009-08-17
There was a post similar to this [earlier]("http://ubuntuforums.org/showthread.php?t=912243"). Could you please have a look into the same and see if it helps you.

Anyway , Could you please unplug your FreeAgent drive and plug it again and run this command.
```
dmesg | tail
``` .

---

### Post by Nethar on 2009-08-17
Sure, thanks. Here is the output... I was checking if it works, so the disconnect/connect is there 2 or 3 times (the first one is disconnect of my printer i think).
```
$ dmesg | tail
[22166.257547] usb 1-4: USB disconnect, address 7
[22166.258145] usblp0: removed
[23747.004045] usb 1-4: new high speed USB device using ehci_hcd and address 8
[23747.153533] usb 1-4: configuration #1 chosen from 1 choice
[23778.612390] usb 1-4: USB disconnect, address 8
[23790.424068] usb 1-4: new high speed USB device using ehci_hcd and address 9
[23790.616853] usb 1-4: configuration #1 chosen from 1 choice
[23825.120646] usb 1-4: USB disconnect, address 9
[23832.084043] usb 1-4: new high speed USB device using ehci_hcd and address 10
[23832.276773] usb 1-4: configuration #1 chosen from 1 choice

```

---

### Post by mikechant on 2009-08-17
One of the most common problems with USB external drives is where it wasn't removed correctly in Windows. When you use this disc in Windows, do you always select the 'remove safely' option (or whatever it's called) or do you just unplug the drive?
If in any doubt, connect the drive while running windows and then 'safely remove' it and then try it again in Ubuntu.

---

### Post by Nethar on 2009-08-17
Hi, thanks for help... Usually I am safely removing my disk but of course it is possible that I just unplug it sometimes. I started my Windows machine, plug FreeAgent disk, working fine, safely removed, unplugged. Plugged into Ubuntu machine... no change, still not automounted as few days ago, can't be used :-(

---

### Post by Nethar on 2009-08-19
No other idea? :cry:
Please ;-)
I am currently testing Ubuntu and I would like to use it in future as my main system instead of Windows. I have found quite good (even better) alternatives for everything I need here, but this external disk problem complicates my work very much, I really need it :cry:

---

### Post by LewRockwell on 2009-08-19
[http://manpages.ubuntu.com/manpages/hardy/man8/fsck.8.html](http://manpages.ubuntu.com/manpages/hardy/man8/fsck.8.html)

here's a newer one:

[http://manpages.ubuntu.com/manpages/jaunty/man8/fsck.8.html](http://manpages.ubuntu.com/manpages/jaunty/man8/fsck.8.html)

.

---

