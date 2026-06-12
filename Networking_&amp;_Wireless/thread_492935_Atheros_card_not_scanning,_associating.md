---
title: "Atheros card not scanning, associating"
date: 2007-07-05
forum: Networking &amp; Wireless
---

### Post by Short Circuit on 2007-07-05
I recently came into possession of a laptop running XUbuntu 6.10, which I would like to upgrade to 7.04.  However, the only way for me to do this is via wireless, and I've been unable to get my Atheros PC Card to work in it.

Details on the Atheros device:

On card: AirPlus XtremeG DWL-G650 (I'd give you the model number, but the sticker wore off...)
lspci: 02:00.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)
According to WinXP: "D-link Airplus Xtreme G DWL-G650 Adapter", Ven 168c, dev 0013, subsys 32021186

From /sys:

/sys/bus/pci/devices/0000:02:00.0/class: 0x020000
/sys/bus/pci/devices/0000:02:00.0/config: "P2D
/sys/bus/pci/devices/0000:02:00.0/device: 0x0013
/sys/bus/pci/devices/0000:02:00.0/irq: 11
/sys/bus/pci/devices/0000:02:00.0/local_cpus: 1
/sys/bus/pci/devices/0000:02:00.0/modalias: pci:v0000168Cd00000013sv00001186sd00003202bc02sc00i00
/sys/bus/pci/devices/0000:02:00.0/resources
0x0000000022000000 0x000000002200ffff 0x0000000000000200
0x0000000000000000 0x0000000000000000 0x0000000000000000

The odd thing is, the deviceID checks out as an 802.11abg card, but in the two years I've had it, it's always functioned as an 802.11bg card, failing to detect 802.11a networks.  In addition, it worked well in my old laptop which, at various times, ran Ubuntu 6.06, 6.10 and 7.04. Its only failing in that system was that I had to insert the card to load the drivers, remove the card, then insert it for the drivers to take hold.

The primary *functional* symptom I've noticed on the new system running XUbuntu 6.06 are that the card never goes into scanning mode, either when the drivers load or when I use iwlist on the command line.  Indeed, running iwlist:

```
root@alice:/# iwlist ath1 scan
ath1     Interface doesn't support scanning : Invalid argument

root@alice:/# 
```

That kinda points out another odd behavior: The card, the only Atheros device in the system, shows up as ath1 instead of ath0.

Any suggestions?

---

### Post by spd106 on 2007-07-05
Can you reinstall the linux-restricted-modules packages that contain the madwifi driver?
Some utilities such as aircrack have to ability to create and destroy interfaces, this means that they sometimes go wrong, so I suggest that you remove any that you may have or at least check for any changes that they may have made.

Also try checking dmesg for errors or maybe even try re-inserting the madwifi driver modules with modprobe (ath_pci).

---

### Post by tturrisi on 2007-07-05
should be

iwlist ath0 scan

unless you have another atheros device.

Post result of:
iwconfig
lspci

---

