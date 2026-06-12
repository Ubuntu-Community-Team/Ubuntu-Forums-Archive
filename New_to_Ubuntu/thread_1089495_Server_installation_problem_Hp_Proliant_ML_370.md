---
title: "Server installation problem Hp Proliant ML 370"
date: 2009-03-07
forum: New to Ubuntu
---

### Post by iRoNMaSTeR on 2009-03-07
i have tried install Ubuntu 8.10 this machine which wait a long time free.
when i finished installation without problem but after grub screen Server will not begin.

it s give me those problems

```

gave up waiting for root device, common problems:
- boot args (cat / proc / cmdline)
- check root delay= (did the system wait long enough?)
- check root= (did the system wait for the right device?)
- missing modules (cat / proc / modules; ls/dev)

ALERT! / dev / disk / by-uuid / 4330b43e-59d7-4d09-894c-bfb70f200f18 does
not exist. Dropping to shell

BusyBox V1.10.2
```
i try several times re-install 8.10 but every time give me same mistakes

when i use Live Cd System opening as normal but i want to use Ubuntu Server.

---

### Post by iamkrazee on 2009-03-07
Try reinstalling grub from LiveCD. And instead of the uuid, try id from /dev/disks to be entered in /boot/grub/menu.lst

---

### Post by iRoNMaSTeR on 2009-03-07
> **iamkrazee said:**
> Try reinstalling grub from LiveCD. And instead of the uuid, try id from /dev/disks to be entered in /boot/grub/menu.lst

i install ubuntu 8.10 (non-server)and formatted disk from Live Cd i used default 
used grub hd0 finished that but still give me same mistake

---

### Post by nubunutim on 2009-03-07
I had a similar experience and found if I turned off the pc and re-powered it started up ok.  Can't explain why.

---

### Post by iRoNMaSTeR on 2009-03-07
Not Solved with this ways.:(
Coming Ubuntu starting Secreen but not start.
still coming 
**(initramfs)**

an other message from forum
> **ago said:**
> when you boot, press esc when given the chance, then press 'e'. Edit the kernel line, remove "quiet splash" and add "debug". Then press enter and "b"
i try it in recovery mode
give some SCSI errors
like

parity error derected data-in phase SCSIRATE scsi timing out
Scsi Timing out command waited 24s

Driver sd Needs Updating please use bus_type methods

---

