---
title: "if live cd works will full install?"
date: 2008-12-28
forum: New to Ubuntu
---

### Post by wkuace on 2008-12-28
Hi I'm a newb to linux. i've downloaded and burned the ubuntu 8.10 live cd and ran it on my laptop. everything seems to to work fine. I want to set up a duel boot of linux and vista so that i can keep using some of the programs i need for classes. My main concerns are will everything work as well with the full install as with the live cd and should i go with 8.10 or 8.04?

---

### Post by Arabica Bean on 2008-12-28
The cd will install a boot loader so you can choose which operating system to boot into, so yes you can keep Vista. 

The only thing to watch out for in installation is to not completely wipe your hard drive, instead, partition your disk into two portions. This can be done easily with the partition manager. 

Finally, go for 8.10.

---

### Post by Arabica Bean on 2008-12-28
> **wkuace said:**
>  My main concerns are will everything work as well with the full install as with the live cd?

In theory, it should actually run better and faster!

---

### Post by gettinoriginal on 2008-12-28
Yes, it should install and work, even faster once installed.  I am running 8.10, upgraded from 8.04, and love it, but some others due to hardware issues have gone back to 8.04.  Whichever Live CD you used, that is the one you should start with, as you know your hardware is supported.  But if you do have any problems, then feel free to visit us here at the forums for help.   And welcome to Ubuntu :popcorn:

---

### Post by igknighted on 2008-12-28
> **wkuace said:**
> Hi I'm a newb to linux. i've downloaded and burned the ubuntu 8.10 live cd and ran it on my laptop. everything seems to to work fine. I want to set up a duel boot of linux and vista so that i can keep using some of the programs i need for classes. My main concerns are will everything work as well with the full install as with the live cd and should i go with 8.10 or 8.04?

Unless you have a special circumstance, the latest stable version (8.10 currently) is recommended.  It has the most support for current hardware and the latest versions of programs (read: more capable).  If you need to install and leave the system as is for years (server, or mass enterprise rollout, for example), then choose 8.04.

If the liveCD works perfectly, then the full install can work perfectly.  I hesitate to say that it 100% will, as there are a few bugs out there that you could run into (that can be worked around), but probably 95% certainty that full install will behave just like the live install.

---

### Post by billgoldberg on 2008-12-28
Just make sure you partition your drive correctly before installing.

Googling "partitioning dualboot guide" will bring up lots of guides you can follow.

---

### Post by hyper_ch on 2008-12-28
use the VISTA partitioner to free some space on your harddisk. Just leave that space unpartitioned and let then the installed handle the rest.

---

### Post by igknighted on 2008-12-28
> **hyper_ch said:**
> use the VISTA partitioner to free some space on your harddisk. Just leave that space unpartitioned and let then the installed handle the rest.

That was an issue when Vista first came out, but gparted can handle Vista's partitions without any issues now.  I've used it multiple times to resize vista, never an issue (plus it was in their release notes at one point IIRC)

---

### Post by wkuace on 2008-12-28
wow this is an amazing response you guys are fast most other boards take forever to respond. I've heard that with the ubuntu bootloader, ubuntu loads by default. how hard is it to set vista as the default. my family uses my laptop when the desktop is being used and they don't really like change (i tried to get them to switch to firefox and they were stumped lol)

---

### Post by igknighted on 2008-12-28
> **wkuace said:**
> wow this is an amazing response you guys are fast most other boards take forever to respond. I've heard that with the ubuntu bootloader, ubuntu loads by default. how hard is it to set vista as the default. my family uses my laptop when the desktop is being used and they don't really like change (i tried to get them to switch to firefox and they were stumped lol)

The ubuntu bootloader is GRUB, which gives you a menu asking to boot Windows or Linux.  Vista's will only boot Windows (xp or vista).  You can fairly easily set Windows to be the default, so it will boot that automatically unless you select otherwise.

---

### Post by wkuace on 2008-12-28
thanks alot i'm going to try to set it up!

---

