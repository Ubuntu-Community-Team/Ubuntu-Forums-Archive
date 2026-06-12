---
title: "Wireless suddenly kicked out"
date: 2008-01-01
forum: Networking &amp; Wireless
---

### Post by chimerical_brio on 2008-01-01
I don't consider myself a total novice at Linux, especially not at managing my wireless card, but I'm currently at a loss. I use a Netgear WUSB11v4 wireless adaptor, accessing the driver through ndiswrapper. At most, the problems that I have involve running "sudo ifdown wlan0" followed by "sudo ifup wlan0"

The problem is, my wireless suddenly stopped working, but I can't understand why. Other computers on the network are having no trouble accessing the router wirelessly; my wireless card seems to be fine (it says it's connected to the right ESSID); I haven't changed any settings in /etc/network/interfaces.

Restarting my computer didn't work; restarting ndiswrapper (with sudo modprobe -r ndiswrapper) didn't work; ifdown/ifup on wlan0 didn't work. Any ideas? I'm totally without a clue. Thanks

---

### Post by chimerical_brio on 2008-01-01
...bump. Help please! I'm totally lost.

---

### Post by chimerical_brio on 2008-01-07
More information: reinstalling ndiswrapper didn't work. The weird thing is, NetworkManager shows that I'm connected, iwconfig shows I'm connected, **my router recognizes when I'm on and when I'm not**, but for some reason I can't get any outgoing connections to work.

Anyone have any ideas at all of things I can try?

---

### Post by fedex1993 on 2008-01-07
umm please bump every 24 hours. 
One thing i can think of is unplug wireliss card and replug back in

---

### Post by chimerical_brio on 2008-01-07
I've tried that multiple times, to no avail. I just have no idea what the problem might be: it seems to be able to pass information with my router, outgoing connections just don't work.

---

