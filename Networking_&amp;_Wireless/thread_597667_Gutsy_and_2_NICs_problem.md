---
title: "Gutsy and 2 NICs problem"
date: 2007-10-30
forum: Networking &amp; Wireless
---

### Post by bortolo on 2007-10-30
Hi all,
I've done a fresh install of Gutsy on my home-server but there's a big problem: I have two NICs of the same model (Realtek 8139+), every time I boot, one interface is named eth0, and the other one is eth1, then eth2, at the 9th reboot it was named eth9. Obviously I can't configure my dhcpd correctly so I googled a little bit and I found [_this_]("http://www.tenshu.net/archives/2007/08/22/ubuntu-consistent-network-hackery/") and [_this_]("https://bugs.launchpad.net/ubuntu/+source/udev/+bug/145382")  posts. One of them suggest to remove /etc/udev.d/rules/70-persistent-net.rules and reboot, well there was no effect for me, the other one suggest to remove the "ADDRESS" parameter and let ubuntu recognize each NIC by its own driver. The problem is that both NICs uses the same driver.
This is my 70-persistent-net.rules:

```

# PCI device 0x10ec:0x8139 (8139too)
SUBSYSTEM=="net", DRIVERS=="?*", ATTRS{address}=="00:e0:3c:49:40:10", NAME="eth0"

# PCI device 0x10ec:0x8139 (8139too)
SUBSYSTEM=="net", DRIVERS=="?*", ATTRS{address}=="d3:5f:a7:af:64:dc", NAME="eth1"

# PCI device 0x10ec:0x8139 (8139too)
SUBSYSTEM=="net", DRIVERS=="?*", ATTRS{address}=="e9:ff:df:0f:bf:1f", NAME="eth2"

```

The first two devices are my real NICs, the third one... I dunno from where it comes, and its name grows at each reboot "(eth2, eth3, eth4...)". This is my interfaces file:

```

# The loopback network interface
auto lo
iface lo inet loopback

```

It doesn't matter what i put inside this file... The behaviour doesn't change :)
Could you please help me? Thanx a lot in advance!

---

### Post by bortolo on 2007-10-30
I just found this [_link_]("https://bugs.launchpad.net/ubuntu/+source/udev/+bug/153727") but it only works for one ethernet card, and I need to use both of them. :(
Thanx again

---

### Post by mpokrywka on 2007-10-31
Try running:
```
udevinfo -a -p /sys/class/net/**eth0**/
```
for both your NICs and use other attributes to give them names, for example:
```
SUBSYSTEM=="net", DRIVERS=="8139too", ATTRS{modalias}=="pci:v000011ABd00004320sv00001043sd0000173Cbc02sc00i00", NAME="eth0"
```
(of course use your correct modalias for earch card)

---

