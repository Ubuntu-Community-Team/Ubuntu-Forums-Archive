---
title: "Broadcom 43xxx wireless card, srange behaviour"
date: 2008-03-10
forum: Networking &amp; Wireless
---

### Post by dimkal on 2008-03-10
Hi.  For about two months my Broadcom 43xx-series wireless is not working. `lspci' produces no trace of Broadcom mini pci wireless card... 

After the last kernel upgrade (2.6.24-12-generic) i got a message saying that new hardware was detected, it was my Broadcom wireless and my "syslog" had this line in it:
[FONT="Courier New"]Mar 10 00:26:31 semele kernel: [  910.093353] b43-phy2: Broadcom 4311 WLAN found[/FONT]
also `lspci' listed my card again... but this was yesterday.

today, i booted my laptop and again, same kernel, but `lspci' now gives me no trace of my wireless card!  I tried looking at bunch of the bcm43xxx setups, but all of them begin by locating the card using `lspci'

can someone please point me to a resource on how to troubleshoot this.

it don't use wireless very often, but few times i needed it; it didn't work.

thanks

---

### Post by luisromangz on 2008-03-10
Are you using Hardy? I mean, the latest Gutsy kernel is 2.6.22, and you know Hardy hasn't yet been released so that kind of thing may happen. 

That said, I lost my wireless connection  a few days ago in the old computer where I test Hardy, and the problem solved when I booted the generic instead of the 386 kernel (both are 2.6.24)

Probably is not the same problem, as I am using a completely different wireless adaptor there, but you may check.

---

### Post by dimkal on 2008-03-10
> **luisromangz said:**
> Are you using Hardy? I mean, the latest Gutsy kernel is 2.6.22, and you know Hardy hasn't yet been released so that kind of thing may happen. 


yes i understand, but it didn't work on Gutsy as well.  Actually it did work at first, but then something happened it stopped working.  Did it stopped working due to some kernel upgrade? i don't know.

I guess a sure way to find out is to reinstall Gutsy and see if everything will work....

---

### Post by luisromangz on 2008-03-10
Maybe it has to do with the kernel upgrade, which driver are you using? bc43xx or ndiswrapper, and how did you install it?

---

### Post by wormser on 2008-03-10
I have a BCM4309 on 2.6.22-14-generic and it works but has a bug when shutting down.  I installed with Restricted Package Manager.  You should try booting a different live CD distro and see if it works.  If lspci is not finding it maybe it popped out of its socket assuming this is a laptop.  Usually there is a trap door on the bottom of laptops to remove them.  Check to see if the card is plugged in but make sure you remove the battery first.

---

### Post by dimkal on 2008-03-11
> **luisromangz said:**
> Maybe it has to do with the kernel upgrade, which driver are you using? bc43xx or ndiswrapper, and how did you install it?

well i have the bc43xx drivers installed, but iwconfig simply gives me this:
```

%> iwconfig
lo        no wireless extensions.

eth1      no wireless extensions.

```

could kernel be missing something?

---

### Post by dimkal on 2008-03-11
> **wormser said:**
> I have a BCM4309 on 2.6.22-14-generic and it works but has a bug when shutting down.  I installed with Restricted Package Manager.  You should try booting a different live CD distro and see if it works.  If lspci is not finding it maybe it popped out of its socket assuming this is a laptop.  Usually there is a trap door on the bottom of laptops to remove them.  Check to see if the card is plugged in but make sure you remove the battery first.

thanks for your advise.  I did check the card, looks like it is sitting pretty well in there.  Also tried to take it out and put it back in. no luck :(

i've also tried to boot an old version of 7.10 (when it initially came out) and it used to work with that version of kernel.  It also did not detect the card.  So i guess the conclusion that the card is dead.

I also remember when around same time when the card stopped working i booted into windows (double boot) and HP suggested a BIOS update.   Does linux bypasses BIOS or it reads it?  

BTW wireless card does not show up on windows as well.

-d

---

### Post by wormser on 2008-03-11
Some system BIOS have an option to turn off wireless.  Others have a switch on the side of the laptop or a Fn key combo that turns off wireless.  If it is not one of those then I believe the card is dead since it is not working in Windows.  If it is dead look for a new card with a chipset Linux friendly.

---

