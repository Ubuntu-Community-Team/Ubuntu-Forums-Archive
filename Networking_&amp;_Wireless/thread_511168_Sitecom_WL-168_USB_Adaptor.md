---
title: "Sitecom WL-168 USB Adaptor"
date: 2007-07-27
forum: Networking &amp; Wireless
---

### Post by drcrazy4 on 2007-07-27
I have a Sitecom WL-168 USB Adaptor which I want to use to get internet although I don't have a clue how to get it working on Ubuntu if I can even get it working at all. I emailed the manufacturer and didn't get anything back. If somebody could run me through what to do or tell me whether it will work or not that would be great. I would like to use Ubuntu instead of Windows but this is holding me back a bit.

Thanks, Joe.

---

### Post by drcrazy4 on 2007-09-04
Sorry to bump but I really do want to make the switch to Linux and without some help on this I don't think it will happen. It would be appreciated if somebody knew something about this, thanks.

---

### Post by kalenetus on 2007-12-05
hi,

i have a sitecom wl-168 (v003 i think)
i'm using ndiswrapper with the winxp driver i got from the sitecom site.

google ndiswrapper or look in the forums here
first i tried the ndis-gtk thing, but results varied.
i think that in the end all it did was install the driver, but i'm not sure

then i did some experimenting leading to the following
/etc/module got an extra line just saying: 
ndiswrapper
(this is to make sure it works after reboot; 
you do 
$sudo modprobe ndiswrapper
$sudo /etc/init.d/network restart 
after installing the driver to test)

/etc/network/interfaces  only says:
auto lo
iface lo inet loopback

now i get some result:
i some see wireless networks!
unfortunately not my own (and it's not hidden!) so i'm still not there ;-(

any suggestions anybody?
i've got adsl modem/router/wifi g from my provider (dvl-### ; providers label is on it)
the wl-168 is also g 
tried with security off, no result, tried wep open and shared .....
i run gutsy gibbon xfce on on a duron 800 machine (anyone in the market for antiques ;-))?

thanks
kalenetus

---

### Post by kalenetus on 2008-01-14
turned out i only see channel 1!

so i set my router to channel 1 only to discover is get no dhcpoffer
;-(

still struggling....

---

