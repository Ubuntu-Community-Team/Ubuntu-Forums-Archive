---
title: "WG311T someone sort it out ..."
date: 2005-06-03
forum: Networking &amp; Wireless
---

### Post by [pl]ice on 2005-06-03
hi, it looks like someone SHOULD ADD something to the wiki network page... that WG311T won't work out of the box!!
  this is great, as i bough it, ( i had wless on acx chip, trouble); so i used, well, wiki's network help, yeh, how nice, finds the card ok, no problem, but same problems occur as other users have (search this forum...) 


now i got to try using linuxant.


thanks

---

### Post by elvis on 2005-06-03
The WG311T uses the Atheros chipset, which is not always supported by the old Madwifi drivers included with Ubuntu.

I find it a little annoying that the wiki states these cards work out of box when they don't.  Not very nice.

Anyways, here's how I upgraded Madwifi and fixed the problem:

[http://ubuntuforums.org/showthread.php?t=38972](http://ubuntuforums.org/showthread.php?t=38972)

Hope it helps.

---

### Post by [pl]ice on 2005-06-04
thanks , doing it right now, 
but for the wifi, for the export KERNELPATH, i assume its
the headers?
:/usr/src/madwifi # export KERNELPATH=/usr/src/linux-headers-2.6.10-5-386
:/usr/src/madwifi # make
Checking if all requirements are met... ok.
mkdir -p ./symbols

i suppose that should work ? :)
thanks

---

### Post by elvis on 2005-06-06
[QUOTE='[pl]ice']
:/usr/src/madwifi # export KERNELPATH=/usr/src/linux-headers-2.6.10-5-386
:/usr/src/madwifi # make

i suppose that should work ? :)
thanks[/QUOTE]

Yeah, if you only downloaded the headers then that's where you should point the kernelpath.  I think I stuffed that up in my howto.  I'll have to double-check that and fix it up.

---

### Post by mcking on 2005-06-09
[QUOTE=elvis]The WG311T uses the Atheros chipset, which is not always supported by the old Madwifi drivers included with Ubuntu.

I find it a little annoying that the wiki states these cards work out of box when they don't.  Not very nice.

Anyways, here's how I upgraded Madwifi and fixed the problem:

[http://ubuntuforums.org/showthread.php?t=38972](http://ubuntuforums.org/showthread.php?t=38972)

Hope it helps.[/QUOTE]

Well, the WG311**T** v2 uses the TI acx111 chipset.  The drivers are included with Hoary by default, but they don't work with the two machines I have with this card.  I have made it my mission today to get them working (come hell or ndiswrapper!)

---

### Post by mcking on 2005-06-09
Well, I'm going to try a tip I saw on the Gentoo Forums.  The poster suggests that you should use the firmware that comes on the driver CD or the downloaded windows driver.  I'll let y'all know if this works or not!

---

### Post by mcking on 2005-06-09
OK, I have made progress, but it still doesn't work.  If I use the WinXP firmware (current version from Netgear website), it loads the card and this time it actually allows the card to scan for accesspoints.  It seems to work (iwlist and iwconfig show the right stuff), but dhcp never gets an IP.  If I set it to a static IP and try to ping the router, no go.  :(

---

### Post by mcking on 2005-06-09
Argh..



As I said before, I have two machines with this card (and Ubuntu).  One of the machines finally gets a signal and can scan the router using the Netgear firmware, but can't actually connect to it (either DHCP or static).

The other one still can't even scan for the router (no access points found in "iwlist ap"), even though it is about 5 feet from the machine I am typing this on!  I tried swapping that one out for an extra WG311T and even tried the D-link firmware (same chipset).

Argh!!  No go!!!

---

### Post by mcking on 2005-06-09
Ok, here's the deal...


I finally had to just bite the bullet and mv the acx_pci module out of /lib/modules/2.6.xxxxx and use ndiswrapper. The acx driver always got found before the ndiswrapper, so it would lock the hardware so ndiswrapper couldn't load.  Once i moved the driver out of the way, it loaded fine.  I would rather use a native driver, but this is better thatn nothing.

I also put "alias acx_pci off" in /etc/modules.d/local  to disable the acx_pci driver  without deleting it so any apt-get kernel upgrades don't put it back in place.

---

### Post by elvis on 2005-06-24
[QUOTE=mcking]Well, the WG311**T** v2 uses the TI acx111 chipset.  The drivers are included with Hoary by default, but they don't work with the two machines I have with this card.  I have made it my mission today to get them working (come hell or ndiswrapper!)[/QUOTE]

In that case, I recommend you follow this guide:

[http://www.houseofcraig.net/acx100_howto.php](http://www.houseofcraig.net/acx100_howto.php)

It details extremely well the use of the open source drivers for acx100 and acx111 chipsets.  I've used this guide myself many a time for some kiosk machines for a particular client of mine running Debian and a simple WM + browser.  Excellent step-by-step information, and recommend above and beyond NDIS wrappers.

---

### Post by [pl]ice on 2005-09-20
heh, i just sold my  :) using acx100 now heheh.

thanks for thelp :D

---

