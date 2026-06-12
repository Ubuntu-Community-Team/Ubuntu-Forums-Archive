---
title: "Feisty rt2500 or rt2500pci"
date: 2007-04-29
forum: Networking &amp; Wireless
---

### Post by erm67 on 2007-04-29
```
erm67@ubuntu:~/debian/projectx-0.90.4$ locate rt2500*.ko
/lib/modules/2.6.20-15-generic/kernel/ubuntu/wireless/rt2x00-legacy/rt2500/rt2500.ko
/lib/modules/2.6.20-15-generic/kernel/ubuntu/wireless/rt2x00/rt2500pci.ko
/lib/modules/2.6.20-15-generic/kernel/ubuntu/wireless/rt2x00/rt2500usb.ko
```

It looks like Feisty Fawn ships both the legacy driver rt2500 and the new rt2500pci from cvs. My card is a:
```
erm67@ubuntu:~$ lspci
02:0a.0 Network controller: RaLink RT2500 802.11g Cardbus/mini-PCI (rev 01)
```

The new driver rt2500pci should support wext and be compatible with network-admin and wpa_supplicant I however had not luck setting it up. ifconfig ra0 down, rmmod rt2500, modprobe rt2500pci
but wpa_supplicant can not connect using WPAPSK. If someone was able to use the driver please post an howto :lolflag:

I already found a useful thread
[http://ubuntuforums.org/showthread.php?p=2323797](http://ubuntuforums.org/showthread.php?p=2323797)

---

### Post by frenzie on 2007-05-13
i am having the same problem, and ive looked around for some useful help guides and how tos and nothing stands out to solve the problem.

I have only WEP options in my drop down list.

The card support WPA under windows

---

### Post by jml on 2007-05-20
I have been trying to get my Averatec's RT2500 card working in all *buntu flavers without success.  Just for giggles, I booted up a copy of PCLinuxOS TR4 and it recognized my card out of the box!  Clicking on the network configuration application walked me through the setup in a matter of minutes I was connected to my WPA encrypted wireless network.  I have to dig a bit to find out what specific apps they are using, but the distro is based on Mandriva but uses apt/synaptic for its package manager.  Its not as well developed as Ubuntu, but its interesting to see that some distrosa have found a solution.

Joe

---

