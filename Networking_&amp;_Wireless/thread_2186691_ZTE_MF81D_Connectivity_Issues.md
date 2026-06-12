---
title: "ZTE MF81D Connectivity Issues"
date: 2013-11-08
forum: Networking &amp; Wireless
---

### Post by derferret on 2013-11-08
Hi!


I recently got a ZTE 821D 4G ready mobile broadband dongle from Telenor (Danish telco) and have been having a lot of trouble getting the thing to work properly with xubuntu 13.04, I am not having the issues some users report where the thing incorrectly registers as a CD-ROM when inserted, it registers correctly as a mobile broadband device and I have no trouble setting up a connection through it.

However, even though I enter the correct dial number, correct APN and the correct PIN code I cannot seem to connect to the internet via the thing. When I click on the newly created mobile broadband connection (Telenor Default 1) it connects just fine, the NM applet turns into a signal strength display and when I look at the connection info I have gotten a DNS, gateway and all the other required info from the ISP. Still though, I am unable to connect to the internet, any attempts to ping any site simply fail with the message "unknown host <whatever".

I have tested the dongle on a windows machine and when using the software provided by the telco (only windows and mac software available) and it works flawlessly on the Windows machine. What I noticed on there is that 1) the connection shows as an Ethernet-like connection while under Linux it shows as a PPP connection and 2) Under windows when the device successfully connect it makes a little "ding" sound, which clearly comes from the USB dongle and not windows (speakers are off).

I have found various forum posts around the internet that seem to indicate that this dongle should work out of the box with Ubuntu, however I can't seem to make the thing work correctly. 

I found this guide [http://www.eigenmagic.com/2012/03/14/how-to-get-telstra-4g-mobile-broadband-working-with-linux/](http://www.eigenmagic.com/2012/03/14/how-to-get-telstra-4g-mobile-broadband-working-with-linux/) which seemed to apply to the same modem I have, and it didn't do anything to help me. Although I could not successfully do the minicom step as for whatever reasons the stick didn't seem to respond properly to commands sent via minicom.


Any help will be welcome.

Again

Distro: Xubuntu 13.04 with all updates.
4G Dongle: ZTE MF821D
Telco: Telenor Denmark

---

### Post by derferret on 2013-11-09
Issue resolved.

Issue was that the [COLOR=#51555C][FONT=Sorts Mill Goudy]/lib/udev/rules.d/40-usb_modeswitch.rules [SIZE=3]already had an entry for the ZTE MF821D in it which information that did not match the values indicated in the guide mentioned in the original post.

Commenting out the existing entry and using only the entry from the posted guide seems to have resolved the issue and I now have fully functioning internet through the LTE dongle.[/SIZE][/FONT][/COLOR]

---

