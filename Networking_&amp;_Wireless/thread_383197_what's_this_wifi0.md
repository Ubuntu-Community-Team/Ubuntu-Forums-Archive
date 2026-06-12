---
title: "what's this wifi0?"
date: 2007-03-13
forum: Networking &amp; Wireless
---

### Post by r.stiltskin on 2007-03-13
My new Edgy installation has a device -- I'm not sure if that's the correct term, so, a *something* -- called **wifi0** that popped up during installation (where I said NOT to make it the primary interface), and is listed by dmesg, ifconfig and iwconfig.

I don't remember ever seeing it before (in Dapper, or before that in Gentoo), and it doesn't seem to be functioning now -- just generating its own collection of errors that don't actually seem to affect anything I'm doing.

My Netgear WGT511T card (identified by lspci as an Atheros AR5212) has always worked fine as ath0, and it still does.  When I run lsmod, I don't see wifi0 or anything similar listed in the output.  I do see wlan, wlan_wep, ath_pci, ath_hal, ath_rate_sample, and wlan_scan_sta.  The last 2 don't seem familiar; the others I've definitely seen before.

iwconfig lists
wifi0  no wireless extensions.
and gives the normal output for ath0

ifconfig lists wifi0 with the same mac address as my ath0, but with a lot of 0s added, and then various errors, for example:```
wifi0     Link encap:UNSPEC  HWaddr 00-14-6C-F8-78-2B-00-00-00-00-00-00-00-00-00-00
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3101 errors:0 dropped:0 overruns:0 frame:658
          TX packets:43 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199
          RX bytes:341873 (333.8 KiB)  TX bytes:3443 (3.3 KiB)
          Interrupt:11 Memory:f1220000-f1230000

```
All those zeros make me suspect that it has something to do with ipv6 (I notice that lsmod lists an ipv6 module -- useless since I don't have an ipv6 router).

Do any of you know what that wifi0 thing actually is, and what's setting it up?

---

### Post by netztier on 2007-03-13
> **r.stiltskin said:**
> 
All those zeros make me suspect that it has something to do with ipv6 (I notice that lsmod lists an ipv6 module -- useless since I don't have an ipv6 router).


Nope, this has nothing to to with IPv6. 

Even with IPv6, MAC addresses are still 48bits long and have not been changed. However, you'll find these 48bit slightly modified (extended to 64bit) in resp. as the host part of an IPv6 address. 

There is however the concept of "link local" addresses in IPv6, hence you'll probably notice that your NICs have IPv6 addresses starting with "fe80:...". These addresses can be used on a local subnet only - allowing you to work with IPv6 within your LAN.

> **r.stiltskin said:**
> 
Do any of you know what that wifi0 thing actually is, and what's setting it up?

The **madwifi-ng** driver module for atheros chipsets (as part of linux-restricted-modules) uses **wifi0** as monitoring-mode interface. The advantage is: you don't have to manually configure the "normal" ath0 interface into monitoring mode when you want to use **kismet** for example. Just tell kismet to use wifi0 as interface instead of ath0.

best regards

Marc

---

### Post by tturrisi on 2007-03-13
wifi0 is NOT just for rfmon mode, it IS the driver for athX devices.  madwifi works by creating a virtual device driver.  This virtual driver also creates a virtual device called wifiX.
see [http://madwifi.org/wiki/ngFeatures](http://madwifi.org/wiki/ngFeatures)

---

### Post by netztier on 2007-03-13
> **tturrisi said:**
> wifi0 is NOT just for rfmon mode, it IS the driver for athX devices.  madwifi works by creating a virtual device driver.  This virtual driver also creates a virtual device called wifiX.
see [http://madwifi.org/wiki/ngFeatures](http://madwifi.org/wiki/ngFeatures)

I stand corrected. I did only glance at the information given on the madwifi website when I stubled across the wifi0 interface a few months ago. Reading is said to help, once more.

My apologies for spreading half-true information

best regards

Marc

---

### Post by r.stiltskin on 2007-03-13
Thanks to both of you, but I still have only a trace of an idea of how this works.  Reading helps, but 90% of the battle is finding the right thing to read.  I read the New Features link that tturrisi posted, and a few other userdocs pages at madwifi.org, so now I have even more questions than before.

For example, "New Features" talks about a program called wlanconfig, but that seems to be obsolete already; apparently just running "modprobe ath-pci" autocreates and configures the devices.  I've been playing around with modprobe -r and modprobe and it's very nice that all I have to do to get my wireless up & running is "modprobe ath-pci".   But I'd like to see how that magic is accomplished.   And I'd like to know what controls which devices are created when the system boots up.  Apparently something is reading my /etc/network/interfaces file; is this all handled in the kernel?

I realize that's a lot to ask, but maybe someone can point me towards the right docs to read.

Also, I'm wondering about this:  when the Ubuntu installer was ready to configure my network, it  gave me an opportunity to choose (unfortunately with no explanation) among eth0, wifi0 and ath0 as the primary interface.  I chose ath0 since that's the one I was familiar with, but it did not autoconfigure correctly and I had to manually configure the connection on the next few screens.  Maybe I should have chosen wifi0?  It's academic now, but this information should be available someplace (and should be readily available to people when they are installing ubuntu).

---

