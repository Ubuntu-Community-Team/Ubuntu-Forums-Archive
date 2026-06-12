---
title: "How to find wireless networks"
date: 2008-04-29
forum: Networking &amp; Wireless
---

### Post by Diki on 2008-04-29
I am using Ubuntu 8.04 on a laptop ([LG R405-4A9](http://ca.lge.com/en/products/model/detail/r405expressdualseries_r405a.cp04a9.jhtml)), and am assuming that my wireless is functioning because I see this in the Hardware Drivers menu:

[[IMG]http://i27.tinypic.com/2evz3lw_th.png[/IMG]]("http://i27.tinypic.com/2evz3lw.png")
(click for big)

I do not know precisely which wireless card I have though.
How do I search for wireless networks to connect to?

---

### Post by einstein on 2008-04-29
Sorry, it doesn't tell you anything.  In my case it actually implies that nothing will work.  I installed Hardy yesterday and this is what ended up working for me....

[LIST=1]
[*]Find out what wireless card you have...
```
dennis@dennis-a200:~$ lspci
...
05:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
```
[*]Get Windows driver (I got mine from my VISTA install) and store it somewhere convenient like your desktop.
[*]DISABLE the HAL and wireless card support stuff in System->Administration->Hardware Drivers.
[*]Shut down the avahi thing...
```
 sudo ip link set wlan0:avahi down
```
[*]Blacklist some stuff in /etc/modprobe.d/blacklist using...
```
blacklist ath_hal
blacklist ath_pci
```
[*]Reboot.
[*]Install ndiswrapper-common, ndiswrapper-utils-1.9 and ndisgtk from Synaptic.
[*]Install your windows wireless driver using ndisgtk - it is under System->Administration->Windows Wireless Drivers
[*]Install wicd from synaptic (I have deb [http://apt.wicd.net](http://apt.wicd.net) hardy extras in /etc/apt/sources.list).
[*]Don't know if reboot is required here but I did anyhow.
[*]Open wicd from Applications->Internet->Wicd.  Wicd should display the available wireless access points.  Fill in the blanks and click connect.
[/LIST]

Hope this helps a bit,
       Dennis

---

### Post by mavi_yelkenler on 2008-04-29
hey guys,
I have also Atheros and you dont need to use ndiswrapper.
Just download the readily-patched snapshot on madwifi ticket ==> [http://madwifi.org/ticket/1679](http://madwifi.org/ticket/1679)

Wicd is a perfect network manager

---

### Post by Diki on 2008-04-29
> **mavi_yelkenler said:**
> hey guys,
I have also Atheros and you dont need to use ndiswrapper.
Just download the readily-patched snapshot on madwifi ticket ==> [http://madwifi.org/ticket/1679](http://madwifi.org/ticket/1679)

Wicd is a perfect network manager

The file specified to download there does not exist: snapshots.madwifi.org/madwifi-ng/madwifi-ng-r2756-20071018.tar.gz

edit: After much fiddling your method worked Einstein. Thanks.

---

### Post by mavi_yelkenler on 2008-04-29
The file specified to download there does not exist: snapshots.madwifi.org/madwifi-ng/madwifi-ng-r2756-20071018.tar.gz> 

ok Diki, on that page you will see a line ==> Alternatively you can download a readily-patched snapshot from here. 

or click here [http://snapshots.madwifi.org/special/madwifi-nr-r3366+ar5007.tar.gz](http://snapshots.madwifi.org/special/madwifi-nr-r3366+ar5007.tar.gz)

regards

---

### Post by einstein on 2008-04-29
You are welcome.

I left out the fiddling part - it is the same old same old on every laptop install I have done and that's quite a few starting with Breezy.  Indeed, none of the Linux wireless stuff ever works for me the way it is supposed to.  I gave up a long time ago and just use ndiswrapper and the windows drivers - it's always a sure bet, including the fiddling part, as I always get wireless working in the end.

Regards,
        Dennis

---

