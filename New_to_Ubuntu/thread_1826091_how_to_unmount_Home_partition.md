---
title: "how to unmount Home partition?"
date: 2011-08-16
forum: New to Ubuntu
---

### Post by sallam on 2011-08-16
Greetings
I need to resize my home partition to make a new partition. I'm using gparted. It seems that I must unmount the home partition before resizing or splitting it. But I failed to unmount it. It says partition busy.
How to tell which operations is using it to stop them?
I do this first time after booting, before opening any programs..

---

### Post by ofnuts on 2011-08-16
> **sallam said:**
> Greetings
I need to resize my home partition to make a new partition. I'm using gparted. It seems that I must unmount the home partition before resizing or splitting it. But I failed to unmount it. It says partition busy.
How to tell which operations is using it to stop them?
I do this first time after booting, before opening any programs..You would have to login as root since root's home is not in /home AFAIK. However in Ubuntu using root isn't recommended, but the whole thing should be doable using a live CD. Just make sure you know which filesystem is on which partition before booting on the CD.

---

### Post by Paqman on 2011-08-16
Yep, you'll need to use a LiveCD or USB. You'll also need to unmount your swap partition (the live session will automatically mount it to improve performance). Open Gparted, right click on your swap and "swapoff". You should then be free to make any changes to your partitions you need.

---

### Post by yetiman64 on 2011-08-16
> **ofnuts said:**
> **You would have to login as root** since root's home is not in /home AFAIK. However in Ubuntu using root isn't recommended, but the whole thing should be doable using a live CD. Just make sure you know which filesystem is on which partition before booting on the CD.

On a _*standard*_ Ubuntu install using the root account is not even possible,

From link no. 4 in my sig,

> **By default, the Root account password is locked in Ubuntu.**Use the live cd option OP. You can't do any gparted operations on a mounted partition and you need /home mounted to use your install.

If you have a swap partition as well and you still can't use gparted on the live cd, right click on swap and select "swapoff". It will depend on your setup if you need to do that, you may not have to.

The command in a live cd terminal, (**edit for clarity**: for gathering device info only,) 

```
sudo fdisk -l
``` -that is a lower case L in the code, will give you information to help with picking devices etc **which then can be used in gparted operations**. Also when working with sudo in a live cd terminal just hit the enter button, no password is used on a live cd terminal.

---

### Post by Wim Sturkenboom on 2011-08-16
Boot into recovery mode, drop to a root shell with network support and you can unmount. That is what recovery mode is for. No need for the liveCD ;)

<snip>. If you don't need the networking, I would bring it down (or pull the cable out or so).

And a warning: make a backup of important data as working on filesystems is always dangerous.

---

### Post by sallam on 2011-09-02
Thanks everyone. The Live CD method worked like a charm.
Here is how I did it, in case any other newbie like me needed detailed steps:
[list]
[*]Put an ubuntu installation CD in your cdrom drive
[*]restart your computer, pressing F12 at boot screen to select "cdrom"
[*]in few minutes, you will be given 2 choices. Select 'Try ubuntu'
[*]When you see the desktop, select the following from the menu at top: System > Admin > GParted partition editor
[*]right-click your home partition, and select 'resize'
[*]format the unallocated space to the system of your choice

[/list]

Many thanks.

---

