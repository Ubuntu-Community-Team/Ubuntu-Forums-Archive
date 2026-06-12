---
title: "Wireless lan is working... Internet is not"
date: 2006-11-21
forum: Networking &amp; Wireless
---

### Post by peskat on 2006-11-21
I have installed Ubuntu 6.10 edgy eft, and after putting in the firmware and configuring it I have my wireless network up and running. My card has the ACX111 chipset by the way. The card is working, I see the router (Linksys WAG354g) and can browse it's settings in Firefox, however I can't access anything past that. The router reports as connected, and the build-in ping goes through nicely. However I can't access any webpage, nor any repositories...](*,) 

My PC is a desktop, however I have no Ethernet, so I can't download anything with apt-get. The router is working, as I'm able to get on the Internet from Windows. My ifconfig shows only the lo and the wlan0 interfaces (although the lo is a bit weird compared to what I had on suse).

Any kind of idea, pointer, solution is welcome. I can post command outputs, although that would require some time (reboot, get in Ubuntu, get the output, reboot get on windows, post)

Thanks

---

### Post by stream303 on 2006-11-21
Can you put your isp's primary and backup dns server addresses in your router setup page and restart networking?  I'd take a look at your /etc/resolv.conf file to see if they show up there.

If that doesn't work, you may want to take a look at this (although I don't use the OpenDNS option, just my isp's dns addresses)

[http://www.ubuntuforums.org/showthread.php?t=282034&highlight=resolv.conf](http://www.ubuntuforums.org/showthread.php?t=282034&highlight=resolv.conf)

---

### Post by j3cakes on 2006-11-22
and check to make sure you have the default gateway set (on wlan0) to your router's LAN ip address.

---

