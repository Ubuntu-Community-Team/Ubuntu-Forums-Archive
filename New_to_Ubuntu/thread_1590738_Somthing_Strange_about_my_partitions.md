---
title: "Somthing Strange about my partitions"
date: 2010-10-08
forum: New to Ubuntu
---

### Post by Legeril on 2010-10-08
So I have 4 partitions on my hard drive, windows on C:, then D: + E: for storage and Ubuntu is on F:.  Now I mounted D and E on my desktop but can no longer unmount them, I get this error "Unable to unmount 84 GB Filesystem.     umount: /media/4E80B0D06C979E44 is not in the fstab (and you are not root)"    Does anyone have any ideas what is happening? Along with this there are now 2 additional partitions in 'Computer' that are labelled different, but from there size I think they are kind of copies of D and E. They are also showing up under my Places tab. I cannot interact with them I get this error "Unable to mount location    Internal error: No mount object for mounted volume"      I've had Ubuntu for about a day and a half now and it was all running so smoothly.

---

### Post by Hippytaff on 2010-10-08
to do commands as route you need to put 'sudo' at the start (you probably already know this)...might be worth looking at the partitions with Gparted from a live cd to see whats what!?

---

### Post by Legeril on 2010-10-08
> **Hippytaff said:**
> to do commands as route you need to put 'sudo' at the start (you probably already know this)...might be worth looking at the partitions with Gparted from a live cd to see whats what!?

I've managed to unmount them with Gparted, although now I can't access C, D or E... This is very strange...

How would I go about making a LiveCD? Do you need a CD or would a DVD work too? I've tried making one before but when I tried to boot it said "Operating system not found"

---

### Post by Hippytaff on 2010-10-08
In linux the drives are not labeled C: D: as in windows, maybe that is what is confusing? it looks more live dev1, dev2, etc
 
to make a live cd/dvd you need to download the iso from the ubuntu website, burn it to disc (on the slowest speed) and then you should be able to boot from disc. - you might need to change the boot order in the bios

---

### Post by Legeril on 2010-10-08
> **Hippytaff said:**
> In linux the drives are not labeled C: D: as in windows, maybe that is what is confusing? it looks more live dev1, dev2, etc
 
to make a live cd/dvd you need to download the iso from the ubuntu website, burn it to disc (on the slowest speed) and then you should be able to boot from disc. - you might need to change the boot order in the bios

Well the drive problem seems to have sorted itself out now :P thanks for your time

---

### Post by Hippytaff on 2010-10-08
Excellent - mark the thread as solved in the thread tools ata the top of the page :-)

---

### Post by coffeecat on 2010-10-08
> **Legeril said:**
> Now I mounted D and E on my desktop but can no longer unmount them, I get this error "Unable to unmount 84 GB Filesystem.     umount: /media/4E80B0D06C979E44 is not in the fstab (and you are not root)"    Does anyone have any ideas what is happening?

You must have mounted them as root somehow. How did you mount them?

> **Legeril said:**
> They are also showing up under my Places tab.

That is much the easiest way of mounting a partition. Simply click on it and when you are finished with it, right-click on the desktop icon to unmount, or click on the eject icon in the left Places pane in a Nautilus (file manager) window.

> **Legeril said:**
> I've managed to unmount them with Gparted, although now I can't access C, D or E... This is very strange...

Not really. If you've only had Ubuntu for a day and a half be very wary of using Gparted. Once you've unmounted with Gparted you cannot remount with the Places menu (I don't know why) but you can from the terminal.

> **Legeril said:**
>  How would I go about making a LiveCD? Do you need a CD or would a DVD work too? I've tried making one before but when I tried to boot it said "Operating system not found"

All you ever wanted to know and more:

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

