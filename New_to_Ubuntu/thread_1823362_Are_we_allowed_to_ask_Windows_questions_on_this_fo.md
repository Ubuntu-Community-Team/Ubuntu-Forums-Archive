---
title: "Are we allowed to ask Windows questions on this forum?"
date: 2011-08-12
forum: New to Ubuntu
---

### Post by brawnypandora0 on 2011-08-12
You see I plan to install Ubuntu on my desktop (which right now has XP) but I first want to transfer all my files from my desktop to my XP laptop before I do a format of my laptop.

I heard that there's some cable that can connect the two computers and some trick using TCP/IP and changing some numbers to transfer files. How do I do this?

---

### Post by LowSky on 2011-08-12
> **brawnypandora0 said:**
> You see I plan to install Ubuntu on my desktop (which right now has XP) but I first want to transfer all my files from my desktop to my XP laptop before I do a format of my laptop.

I heard that there's some cable that can connect the two computers and some trick using TCP/IP and changing some numbers to transfer files. How do I do this?

Its called a crossover cable... basically just cat5 with the pins aligned in such a way that you can do transfers without a router. No you can't use a normal cat5 ethernet cable.

If you already have network, be it wireless or wired just share the folders or files you with to share.. very simple..

or just do everything by flash drive or cd-r or dvd-r or even floppy if you have to..

All up to you. Network transfer is probably the fastest, and sharing files in Windows is very simple. right click on the file and share

---

### Post by brawnypandora0 on 2011-08-12
> **LowSky said:**
> Its called a crossover cable... basically just cat5 with the pins aligned in such a way that you can do transfers without a router. No you can't use a normal cat5 ethernet cable.

If you already have network, be it wireless or wired just share the folders or files you with to share.. very simple..

or just do everything by flash drive or cd-r or dvd-r or even floppy if you have to..

All up to you. Network transfer is probably the fastest, and sharing files in Windows is very simple. right click on the file and share

I don't already have a network. How do I make one? Do networks create "virtual harddrive space"?

---

### Post by papibe on 2011-08-12
> **brawnypandora0 said:**
> How do I make one?
You just buy it. For [example]("http://www.microcenter.com/single_product_results.phtml?product_id=0215128").

Regards.

---

### Post by Paqman on 2011-08-12
> **LowSky said:**
> No you can't use a normal cat5 ethernet cable.


Actually these days you can. Network adaptors have been able to automatically swap the pins over for a while now. As long as the machines aren't old and horse-drawn it should work fine.

---

### Post by Bilou5404 on 2011-08-12
> **brawnypandora0 said:**
> You see I plan to install Ubuntu on my desktop (which right now has XP) but I first want to transfer all my files from my desktop to my XP laptop before I do a format of my laptop.

I heard that there's some cable that can connect the two computers and some trick using TCP/IP and changing some numbers to transfer files. How do I do this?

There's a typo there. You said "transfer all my files from my desktop to my XP laptop before I do a format of my laptop."

Which is obviously nonsense!

Don't bother messing about with network stuff:

a.Compared to making a dvd it will be VERY slow.
b.If something goes wrong you are screwed.

You need a cast-iron backup of everything that is important. Copy it all to dvds. If you don't then you are an idiot.

You might then consider using a Windoze disk utility like Paragon (my favorite) on the desktop to make some space on the HD. Then boot on a pendrive linux and use that space to make a swap partition of (say)5GB, an ext3 linux data partition of (say) 50GB and an ext3 linux system partition of (say) 50GB. But do the dvd backup first! 

Don't use ext4 which is the default on Ubuntu. Windoze utilities can't handle it yetso it will screw up any dual boot.

Follow those basics and you are bullet-proof. If it all goes wrong, then your data is still there on the DVDs.

Once the desktop is up and running and you've got a good feeling as a beginner in Linux, synchronize the data on the two machines, make another dvd backup, and then go dual boot on the laptop, (say) windoze 7 and Ubuntu or Mint. Dual boot worked great on my main desktop. But I had to sell it when I moved countries; Sob!

Good luck, and pm me any time. I'm a Linux noob and enjoying it, but there are few better than me on Windoze.

Guillaume

---

### Post by The Cog on 2011-08-12
I agree that you should have a backup copy of your important files. I prefer an external hard drove, but DVDs will do. It may be quicker to make the backup and restore to the other machine than it is to mess about setting up networking.

Good luck with your install. You'll always find help in these forums if you need it.

---

### Post by walt.smith1960 on 2011-08-12
Another option would be to create an NTFS partition just for data storage.  Linux will read and write NTFS just fine and you don't have to ask delicate fussy Windows to do anything outside its comfort zone, like read & write to a non-FAT or non-NTFS partition.  Plus, if you want to back up your data, just back up that partition and you have it all, Windows and Linux.

---

