---
title: "Trouble with ndiswrapper/WUSB11v4"
date: 2007-06-14
forum: Networking &amp; Wireless
---

### Post by chimerical_brio on 2007-06-14
So I've been following the instructions for installing Linksys's WUSB11v4 USB wireless adaptor [here]("http://ubuntuforums.org/showthread.php?t=383466&highlight=wusb11v4") (the instructions are the first reply). So everything works, I get it "installed," but then when I unplug the physical cable with the USB plugged in, I can't access the internet. I did ```
sudo ifup wlan0
```, but still nothing. When I type ```
iwconfig
``` it shows my wireless as set up on wlan0. The only thing I can think of is the fact that when I type ```
netstat -rn
``` to see the routing table, it's kind of weird: I have two sets of ifaces, one for eth0 and one for wlan0. Any ideas? Thanks a lot.

---

### Post by chimerical_brio on 2007-06-14
The really weird thing, which I just noticed, is that the router is recognizing my computer as attached. Also, I somehow managed to install SSH, though I still can't sudo apt-get update (it just stops at 30% connected and then nothing happens until I ctrl-C out of it), and I can't SSH into the box from another computer on my network. Help??

---

### Post by chimerical_brio on 2007-06-14
Bump...

---

### Post by chimerical_brio on 2007-06-14
Ugg. I'm sorry to be annoying..but I've been trying to get this for the better part of two weeks, to no avail. I can't figure anything out at all, it seems like it should be working perfectly but...it's not. Help!

---

