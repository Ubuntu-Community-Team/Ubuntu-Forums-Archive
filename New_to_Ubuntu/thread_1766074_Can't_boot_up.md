---
title: "Can't boot up"
date: 2011-05-23
forum: New to Ubuntu
---

### Post by grantmcduling on 2011-05-23
Hi team.

I am faced with an unusual problem. When I turn on the power of my tower, I get the normal booting up screen, then I get this: Analogue out of range 92.3 Khz - 58 KHz.

I can't get past this screen. Any ideas how I can boot up my system? I am using Ubuntu 11.04. Never had problems booting up until now.

---

### Post by garvinrick4 on 2011-05-23
Does a Live CD (your install Cd for Ubuntu using Try Ubuntu) boot up?

---

### Post by grantmcduling on 2011-05-23
No, not really. When I load the install disc (which in my case was for v 10.10) I get two options: install the software or try it out. I tried it but can't access my 'real' data in my computer with it, just the trial stuff. I guess if I reload the v 10.10, I'll loose my data. Correct?

---

### Post by garvinrick4 on 2011-05-23
> **grantmcduling said:**
> No, not really. When I load the install disc (which in my case was for v 10.10) I get two options: install the software or try it out. I tried it but can't access my 'real' data in my computer with it, just the trial stuff. I guess if I reload the v 10.10, I'll loose my data. Correct?
Does it boot up? Run this and tell me what it says:
sudo fdisk -l (lower case L)

---

### Post by grantmcduling on 2011-05-23
I ran the script and this is what it said:

grant@grant-GQ565AA-ABG-SR5220AN:~$ sudo fdisk -l
[sudo] password for grant: 

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0007e18e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4661    37431296   83  Linux
/dev/sda2            4661        4866     1648641    5  Extended
/dev/sda5            4661        4866     1648640   82  Linux swap / Solaris

Disk /dev/sdf: 4009 MB, 4009754624 bytes
124 heads, 62 sectors/track, 1018 cylinders
Units = cylinders of 7688 * 512 = 3936256 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000dd35c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1               1         960     3685376    b  W95 FAT32
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(0, 32, 33) logical=(0, 33, 3)
Partition 1 has different physical/logical endings:
     phys=(458, 238, 36) logical=(959, 0, 8)
Partition 1 does not end on cylinder boundary.
/dev/sdf2             960        1019      227329    5  Extended
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(459, 16, 4) logical=(959, 33, 9)
Partition 2 has different physical/logical endings:
     phys=(487, 92, 53) logical=(1018, 50, 20)
Partition 2 does not end on cylinder boundary.
/dev/sdf5             960        1019      227328   82  Linux swap / Solaris
grant@grant-GQ565AA-ABG-SR5220AN:~$

---

### Post by Hedgehog1 on 2011-05-24
The '**Analogue out of range 92.3 Khz - 58 KH**' is from the monitor. It is getting a scan rate too high/low for it to display.

***The Hedge***

:KS

---

### Post by garvinrick4 on 2011-05-24
Are you fixed?

---

### Post by wildmanne39 on 2011-05-24
> **grantmcduling said:**
> Hi team.

I am faced with an unusual problem. When I turn on the power of my tower, I get the normal booting up screen, then I get this: Analogue out of range 92.3 Khz - 58 KHz.

I can't get past this screen. Any ideas how I can boot up my system? I am using Ubuntu 11.04. Never had problems booting up until now.
Hi, I have the same problem, but when mine is going into boot I hit enter and it boots,but I have not been able to fix it, I was hoping it would be fixed when natty was released,it only started with the natty beta. I set the hertz right in nvidia settings but in display settings I can not change it I believe it is because natty is reporting incorrectly.

---

### Post by grantmcduling on 2011-05-24
I can get my system up and running by hitting enter a few times one after the other. I looked closer at the analogue out of range message (thanks hedgehog 1) and discovered that my LG Flatron Wide monitor needs drivers. I have the drivers disc but it's only for Windows. Any idea if this is the problem? If so where can I get a suitable driver? I have looked on LG's web site and done a google search but found nothing.

---

### Post by Hedgehog1 on 2011-05-24
> **grantmcduling said:**
> I can get my system up and running by hitting enter a few times one after the other. I looked closer at the analogue out of range message (thanks hedgehog 1) and discovered that my LG Flatron Wide monitor needs drivers. I have the drivers disc but it's only for Windows. Any idea if this is the problem? If so where can I get a suitable driver? I have looked on LG's web site and done a google search but found nothing.

What you are seeing is the scan rate of grub (grub has been updated for Natty).

You can fix it by doing this from you running Ubuntu (after you hit enter a few times):

```
gksudo gedit /etc/default/grub
```

[COLOR="Red"]and change this line:[/COLOR]

#GRUB_GFXMODE=640x480

[COLOR="red"]to this:[/COLOR]

GRUB_GFXMODE=640x480

[COLOR="red"]Then save and exit the document.[/COLOR]


Then do:

```
sudo update-grub
```


***The Hedge***

:KS

---

### Post by jtarin on 2011-05-24
I've got three LG Flatron Wide monitors and all three have no problem with Ubuntu 10.10.Nevermind ...I think Hedgehog is on to it.

---

### Post by grantmcduling on 2011-05-24
Fabulous, you are a genius hedgehog1. Worked beautifully.

Grant

---

### Post by Hedgehog1 on 2011-05-24
*[SIZE="4"]Hurray![/SIZE]*

***The Hedge*** gets another lucky guess! :D

---

### Post by jtarin on 2011-05-24
> **grantmcduling said:**
> Fabulous, you are a genius hedgehog1. Worked beautifully.

GrantHey! He couldn't have done it without my "badgering".

---

