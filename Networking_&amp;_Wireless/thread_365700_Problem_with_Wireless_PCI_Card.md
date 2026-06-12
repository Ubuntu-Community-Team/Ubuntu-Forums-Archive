---
title: "Problem with Wireless PCI Card"
date: 2007-02-19
forum: Networking &amp; Wireless
---

### Post by HappenST on 2007-02-19
I am having problems with wireless.  I have some experience with ubuntu, but apparently not enough.

I just installed 6.10 AMD64.  I can't get my wireless PCI card - Gigabyte GN-WP01GS - to work.  I plugged in a USB wireless adapter and it worked fine.  I have the following wireless devices:

wlan0
wmaster0

I followed this post: [http://www.ubuntuforums.org/showthread.php?t=132980](http://www.ubuntuforums.org/showthread.php?t=132980) and tried to install the driver listed there.  I'm pretty sure it installed fine, but I can't tell.  All the directions said I should have a device "ra0", but I still just have wlan0 and wmaster0 (and eth0, eth1, eth2, ath0.)  I know you guys need more information, but I don't know what to give you.  It refuses to connect to the access point.  What should I do?

Thanks!

---

### Post by almax00 on 2007-02-20
this worked for me: (gigabyte wireless pci card)
[http://www.ubuntuforums.org/showthread.php?t=296822](http://www.ubuntuforums.org/showthread.php?t=296822) - it is a fairly long thread but has alot of good info.

did you restart networking or reboot after making all the changes ?

---

### Post by HappenST on 2007-02-21
Ra0 is here!  It's working.  I swear that I had tried rebooting before, but when I booted it today, it was good to go.  Thanks for the help.

---

