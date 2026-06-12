---
title: "Lost wireless after upgrading Nvidia card"
date: 2008-02-16
forum: Networking &amp; Wireless
---

### Post by Randykc on 2008-02-16
I installed 7.10 last weekend and after many unsuccessful attempts, I was finally able to get my Broadcom 43xx wireless card connected using fwcutter from the guide at [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Gutsy#head-57a53fe7781b5958f4b5cab083c856b54b1da0c6](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Gutsy#head-57a53fe7781b5958f4b5cab083c856b54b1da0c6)

This weekend, I wanted to change my video card from a Savage4 to an Nvidia Geforce4. The new card installed ok, but I lost my wireless connection to my router.  Putting the Savage4 video card back in again re-established my wireless connection. 

I noticed that with the Nvidia card running, I had another Proprietary driver listed in the Restricted Drivers settings listed as not in use.  Could this be causing the problem? Any suggestions on resolving is greatly appreciated.

---

### Post by Sokertes on 2008-02-16
Could be an IRQ conflict. I had an issue like that and it took me forever to figure it out.

With the new card in do run lspci and see if the wireless card is listed.

If it is not listed then it is more than likely an IRQ conflict. Either you have to switch some cards around (easier) or set the IRQ manually (harder and doesn't always work.

Sokertes

---

### Post by Randykc on 2008-02-16
lspci appears normal with the Nvidia card installed.  I am able to see the wireless card.  I can also see my router and other wireless networks in range. I am just not able to fully activate the wireless connection. It gets to 57% and then stops.

---

### Post by Sokertes on 2008-02-17
give ndiswrapper a try for you wireless card

it uses the windows drivers. I use it on my laptop and it works great and it is stable. I connect to my friends wireless G network (with their permission of course) that is about 5 yards away with a constant connection, weather permitting. If the weather is bad the connection strength falls and the speed slows down a tad.

I have also used it on a buffalo wireless G pc card and it worked right off the bat out of the box.

For over a year I used linuxant for my laptop which cost my $20 but ended up using ndiswrapper cause it was more stable.

---

