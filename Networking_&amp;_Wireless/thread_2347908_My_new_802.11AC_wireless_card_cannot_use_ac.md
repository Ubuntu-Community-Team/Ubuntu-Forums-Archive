---
title: "My new 802.11AC wireless card cannot use ac"
date: 2016-12-29
forum: Networking &amp; Wireless
---

### Post by dabbeg on 2016-12-29
Hi,

I'm running a ubuntu server 16.06.
I just bought a new Asus PCE-AC68 Dual-Band PCI-E Adapter which should be using 802.11ac.

To get ubuntu to show the interface I installed bcmwl-kernel-source package.
When I list the interface with iwconfig it shows the interface as "IEEE 802.11abg"


[HTML]
lspci -nn -d 14e4:

03:00.0 Network Controller [0200]: Broadcom Corporation BCM4360 802.11ac Wireless Network Adapter [14e4:43a0] (rev 03)
[/HTML]

How do I get the interface running on 802.11ac instead of 802.11abg?

---

### Post by praseodym on 2016-12-30
Please install the respective driver for your kernel version:

Up to Kernel 4.6
```

sudo apt-get install linux-headers-$(uname -r) build-essential dkms
wget http://de.archive.ubuntu.com/ubuntu/pool/multiverse/b/broadcom-sta/broadcom-sta-dkms_6.30.223.271-3_all.deb
sudo dpkg -i broadcom-sta-dkms_6.30.223.271-3_all.deb 
```

From Kernel 4.7:

```
sudo apt-get install linux-headers-$(uname -r) build-essential dkms
wget http://de.archive.ubuntu.com/ubuntu/pool/multiverse/b/broadcom-sta/broadcom-sta-dkms_6.30.223.271-4_all.deb
sudo dpkg -i broadcom-sta-dkms_6.30.223.271-4_all.deb 
```

First: Uninstall bcmwl-kernel-source, its too old

---

### Post by dabbeg on 2016-12-30
This is solved!

I though that what I mentioned above was the reason for my interface could not search anc connect to a 5Ghz network.

I tried using:
```

iw wlan0 scan

```
but it did not show my 5Ghz network.

Then I found out that the interface does not support all channels.
It is possible to list available channels with:

```

iw list

```

Then I went to my router settings and choose the channel that was available in the output of 'iw list'.

After that the interface could search and connect to the 5Ghz network.

---

