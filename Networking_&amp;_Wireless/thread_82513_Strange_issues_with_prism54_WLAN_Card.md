---
title: "Strange issues with prism54 WLAN Card"
date: 2005-10-26
forum: Networking &amp; Wireless
---

### Post by f.prisson on 2005-10-26
Hi everybody,

I installed Breezy Badger a few weeks ago and I'm very happy with it. Some minor problems but I could solve them all by myself. 

But I have a strange problem with my WLAN NIC. When I boot the system, my wired NIC is recognized as eth1, my WLAN NIC as eth2, but ifconfig shows no complete MAC address (last six digits are zeros), the beginning of the MAC address doesn't match any NIC. No actions are possible with the eth2 device, eth0 doesn't exist.

If I do ```
sudo rmmod prism54
``` and ```
sudo modprobe prism54
``` the card is recognized as as eth0 and I can configure it.

I had a look in /var/log/messages and dmesg and found that during the boot process my wired NIC seems to be recognized as eth0 and then switches to eth1:```
[4294676.221000] eth0: VIA Rhine II at 0x1ec00, 00:0d:87:62:f5:dc, IRQ 10.
[4294676.222000] eth0: MII PHY found at address 1, status 0x786d advertising 05e1 Link 45e1.
[4294700.443000] eth1: link up, 100Mbps, full-duplex, lpa 0x45E1

``` Nothing to see about the WLAN NIC here. Removing the module and reloading it brings:```
[4294740.378000] eth2: removing device
[4294744.651000] eth0: resetting device...
[4294744.651000] eth0: uploading firmware...
[4294744.806000] eth0: firmware version: 1.0.4.3
[4294744.806000] eth0: firmware upload complete
[4294745.045000] eth0: interface reset complete

``` The problem occurs in different PCI slots and survived a new install. I used this card without problems in Hoary. 

Does anybody have an idea what might be the problem?

---

### Post by tigerstripedcat on 2005-10-27
I can't be of much help, but I can tell you I have the same problem (not sure about the eth0/eth1 problem though, my wireless is configured for ra0).  If I find out anything, I'll let you know.  All I can see is finding the latest drivers and recompiling maybe.

My thread is here:

[http://www.ubuntuforums.org/showthread.php?t=82734](http://www.ubuntuforums.org/showthread.php?t=82734)

Good luck,

---

