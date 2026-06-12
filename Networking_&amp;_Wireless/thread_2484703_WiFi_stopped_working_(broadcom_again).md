---
title: "WiFi stopped working (broadcom again?)"
date: 2023-03-07
forum: Networking &amp; Wireless
---

### Post by jan-80 on 2023-03-07
I installed an older PC for a colleague. Everything was fine, and the performance was snappy. Probably also due to the 120 GB SSD I had left over.

System: Dell Latitude 6520 - 4 GB RAM - i3 2nd gen. - 120 GB SSD - Ubuntu 22.04.1

After a few weeks, WiFi stops working. Looking at the machine, it's as if the machine doesn't have WiFi at all. It doesn't show up in the network settings. It does show up in the BIOS settings, though. But simply a "Broadcom Wireless".  As it always did.

I suppose that the Broadcom drivers have been upgraded and don't work any more. Starnge, because in the weeks after the install, everything was fine. How do I correct this. I'd hate to take this machine back an start the install over again...

Looking at Software & updates, extra drivers, I find:[INDENT]Broadcom and subsidiaries: BCM43228 802.11 a/b/g/n (Wireless 1530 Half-size Mini PCIe Card)
*This device isn't working.*[/INDENT]
[INDENT=2]o Broadcom 802.11 Linux STA use wireless driver source from bcmwl-kernel-source (non-free)
o don't use this device[/INDENT]

If I choose the first, of course, I get an error that I cannot download packages while off-line ... duh!

Apart from hooking it up to a cabled network, how could I download it on another machine and install it on this one?

Greetings from the TyRannoSaurus,
Jan-80

---

### Post by chili555 on 2023-03-07
Please run and post:

```
lspci -nnk | grep 0280 -A3
sudo dpkg -s bcmwl-kernel-source | grep Status
sudo dmesg | grep -e wl -e bcm
```

---

### Post by jan-80 on 2023-03-08
[FONT=courier new]master@Dell-Latitude-E6520:~$ lspci -nnk | grep 0280 -A3[/FONT]
[FONT=courier new]02:00.0 Network controller [0280]: Broadcom Inc. and subsidiaries BCM43228 802.11a/b/g/n [14e4:4359][/FONT]
[FONT=courier new]	Subsystem: Dell Wireless 1530 Half-size Mini PCIe Card [1028:0011][/FONT]
[FONT=courier new]	Kernel modules: bcma[/FONT]
[FONT=courier new]0a:00.0 FireWire (IEEE 1394) [0c00]: O2 Micro, Inc. 1394 OHCI Compliant Host Controller [1217:13f7] (rev 05)[/FONT]
[FONT=courier new]master@Dell-Latitude-E6520:~$ sudo dpkg -s bcmwl-kernel-source | grep Status[/FONT]
[FONT=courier new][sudo] wachtwoord voor master: [/FONT]
[FONT=courier new]dpkg-query: pakket 'bcmwl-kernel-source' is niet geïnstalleerd en er is geen info beschikbaar[/FONT]
[FONT=courier new]Gebruik dpkg --info (= dpkg-deb --info) om archiefbestanden te bekijken.[/FONT]
[FONT=courier new]master@Dell-Latitude-E6520:~$ sudo dmesg | grep -e wl -e bcm[/FONT]
[FONT=courier new]master@Dell-Latitude-E6520:~$ [/FONT]

---

### Post by chili555 on 2023-03-08
> pakket 'bcmwl-kernel-source' is niet geïnstalleerd That is the required driver for your wireless device. There are three things you can do to install it. First is the one minute option. Beg or borrow an ethernet connection from a friend or relative. Bribe them with a six-pack of their favorite beverage if needed.

This post describes the hardest: [https://askubuntu.com/questions/986827/dependencies-unsatisfied-for-offline-broadcom-installation/986834#986834](https://askubuntu.com/questions/986827/dependencies-unsatisfied-for-offline-broadcom-installation/986834#986834) Of course, substitute your Ubuntu version. It is surely not 'Artful' as in the post.

The third, and easiest way is to tether your phone. Once connected, do:

```
sudo apt update
sudo apt install bcmwl-kernel-source
```

Reboot. You should be all set.

---

### Post by jan-80 on 2023-03-08
Fine, that worked. Thanks a lot. :D

I didn't have to beg or bribe anyone. I hooked the machine up to a netbook that acts as a WiFi router.
FYI, this is my favorite brew. Available in most supermarkets around here. ;-) 
[https://en.wikipedia.org/wiki/Westmalle_Brewery](https://en.wikipedia.org/wiki/Westmalle_Brewery) [IMG]https://en.wikipedia.org/wiki/File:Westmalle_-_2_bouteilles.jpg[/IMG]

---

### Post by chili555 on 2023-03-08
Awesome! Please use thread tools at the top to mark Solved. I get a 5% rise in my pay. $0 + 5% = $0!

I shall look for Westmalle. Thanks.

---

