---
title: "how uninstall the rt61 drivers"
date: 2007-12-06
forum: Networking &amp; Wireless
---

### Post by juniorsonny on 2007-12-06
I need to know how to uninstall the ralink rt61 drivers so I can install the serialmonkery drivers.

---

### Post by Original Brownster on 2007-12-07
Hi,
If you want to stop the driver supplied with the kernel from loading, try blacklisting the module by adding it's name to the file
/etc/modprobe.d/blacklist
[URL="http://rt2x00.serialmonkey.com/wiki/index.php?title=HOWTOS"]
Serial monkey howtos[/URL]

---

### Post by juniorsonny on 2007-12-07
Thanks I'll try that.  I hope I have better luck with the serialmonkey drivers.

---

### Post by juniorsonny on 2007-12-07
I just remembered that the ralink rt61 drivers are restricited drivers so maybe I can just click off so it will say they are not in use.

---

### Post by juniorsonny on 2007-12-13
how do you blacklist list the ralink rt61 driver when the serial monkey driver is also called rt61?

Edit: Or can you do a "make uninstall" in terminal?

---

### Post by Original Brownster on 2007-12-13
> **juniorsonny said:**
> how do you blacklist list the ralink rt61 driver when the serial monkey driver is also called rt61?

Edit: Or can you do a "make uninstall" in terminal?

Hi, are they absolutely identical names? I have rt61pci.ko on my sys, does serial monkey build to exactly this?  If this is the case I do not know the 'correct' way of  dealing with this, I would try moving the original module out of the way, it might work just renaming it. The modules live in the /lib/modules/{insert kernel version here}/ path continues..../

---

### Post by juniorsonny on 2007-12-13
I think the original is rt61.o and the new one is rt61.ko. I've already deactivated the rt61pci.  It just keeps loading the rt61.o. I need the rt61.ko to load. Can I blacklist these individual modules?

---

### Post by Original Brownster on 2007-12-13
> **juniorsonny said:**
> I think the original is rt61.o and the new one is rt61.ko. I've already deactivated the rt61pci.  It just keeps loading the rt61.o. I need the rt61.ko to load. Can I blacklist these individual modules?

try and blacklist it too and see what happens you can always reverse it if it doesn't work, my guess is that none will load but why not try it. If it fails rename / move the original one then you  can guarantee it wont load :)

---

### Post by juniorsonny on 2007-12-13
thanks, I'll see what happens.

---

### Post by juniorsonny on 2007-12-28
I finally got my wireless working, but it has been a difficult process.  First, I found out the blacklisted drivers were still loading.  I found the individual files and renamed them so them si they wouldn't load up.  I also noticed in the file that shows modules to boot at startup it had: ls, fuse, rt61, ndiswrapper. I deleted the rt61 entry.  After all this I was able to use the windows rt61 driver using ndiswrapper.  Also, I removed the gnome network manager from startup and I'm using Rutilt as a wireless network manager.  The gnome manager caused the computer to lockup.  But now finally I have a stable wireless connection with no dchp errors,  sluggish speed or constant dropped connections.

---

### Post by jocheem67 on 2007-12-29
[HTML]sudo su
echo "blacklist rt61pci" >> /etc/modprobe.d/blacklist
exit[/HTML]

should do the trick....taken from the rt2500 howto on this forum.

Compiling the serialmonkey driver isn' t that hard by the way, I used the rt2500 howto and just substituted 2500 with 61...fairly easy....

Her' s my /etc/network/interfaces:

[HTML]auto wlan0
iface wlan0 inet dhcp

pre-up ifconfig wlan0 up
pre-up iwconfig wlan0 essid "Jochem" 
pre-up iwconfig wlan0 mode Managed
pre-up iwpriv wlan0 set AuthMode=WPAPSK
pre-up iwpriv wlan0 set EncrypType=TKIP
pre-up iwpriv wlan0 set WPAPSK="your wpa key" 
pre-up ifconfig wlan0 up
[/HTML]

---

