---
title: "Can't connect to Wireless Network"
date: 2011-01-09
forum: New to Ubuntu
---

### Post by wyomingjoe on 2011-01-09
My father and I have just downloaded Ubuntu 10.10 desktop addition to both our laptops yesterday and are unexperienced linux/ubuntu users. My father has a toshiba w/ a 64bit operating system and I have a dell w/ a 32bit operating system.

Neither of us can connect to our home Wireless Network, but we both can connect to his verizon moble brodband via usb.

Our Wireless network has WEP security with a 10 digit password witch we have both entered correctly mutable times when prompted.

Last night wile the operating system was installing onto my computer I successfully connected and surfed the net, and my father says he was on our home connection this morning also. I'm not sure why its not working now or what we are doing wrong but I would appreciate any helpful advice as I have a school project I desperately need to finish.

Please Help
- Cat

---

### Post by TeoBigusGeekus on 2011-01-09
Have you enabled the additional wireless drivers for your systems?
Administration>System>Additional Drivers

---

### Post by wyomingjoe on 2011-01-09
> **TeoBigusGeekus said:**
> Have you enabled the additional wireless drivers for your systems?
Administration>System>Additional Drivers

It says "searching for additional drivers" and then "no proprietary drivers are in use on this system"

---

### Post by TeoBigusGeekus on 2011-01-09
What are your wireless chipsets?
Could you post the output of
```
lshw
```
?

---

### Post by tad1073 on 2011-01-09
better yet, post the output of this command:
```
lshw -C network
```
that cuts out the unnecessary junk and only lists the wireless chipset

---

### Post by isee on 2011-01-09
May be a little simplistic but have you tried rebooting your router?

---

### Post by wyomingjoe on 2011-01-09
I have tried rebooting the router; I'm not sure what you mean by  wireless chipsets.
"post the output of this command:" I typed the command you gave me into Terminal and I'm not sure what part to post.

*-network
description Ethernet interface
product: 88E8039 PCI-E Fast Ethernet Controller
vendor: Marvell Technology Group Ltd.
physical id: 0
bus info: pci@0000:0200.0
logical name: etho
version: 14
serial:00:a0:d1:9e:0e:4f
width: 64 bits
clock: 33MHz
capabilities: bus_master cap_list ethernet physical
configuration: brodcast=yes driver=sky2 driverversion=1.28 firmware=N/A
latency=0 multicast=yes
resources: irq:45 memory:f0000000-f0003fff ioport:2000(size=256)
*-network
description: wireless interface
physical id: 3
bus info: usb@2:6
logical name: wlan0
serial: 00:16:44:9d:f7:8b:
capabilities: ethernet physical wireless
configuration: brodcast=yes driver=rtl8187 driverversion=2.6.35-24-gener
ic firmware=N/A multicast=yes wireless=IEEE 802.11bg

---

