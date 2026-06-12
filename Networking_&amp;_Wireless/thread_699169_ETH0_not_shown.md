---
title: "ETH0 not shown"
date: 2008-02-17
forum: Networking &amp; Wireless
---

### Post by neilrudden on 2008-02-17
Hi ,

Have just installed Ubuntu7.1, Install seemed to go without any errors, but the ethernet card does not seem to have been detected/installed correctly.

if I run lspci from the terminal i see the network card as one of the entries.When I look at the network card on the top right it say no network devices found.

It is an intel motherboard with a Intel Pro 1000(82573V) chip set.

I saw a post on one of the posts about compling the driver manualy, but have no idea how?
Thanks,

Looking forward to my new linux box

Neil

---

### Post by jan quark on 2008-02-17
please post the output of 

```
lspci
```

---

### Post by neilrudden on 2008-02-17
Here we go,

As far as i can see, I have highlighted the network card, does this command list all equipment on the pci bus?

00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub
00:01.0 PCI bridge: Intel Corporation 82945G/GZ/P/PL PCI Express Root Port
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1c.4 PCI bridge: Intel Corporation 82801GR/GH/GHM (ICH7 Family) PCI Express Port 5 (rev 01)
00:1c.5 PCI bridge: Intel Corporation 82801GR/GH/GHM (ICH7 Family) PCI Express Port 6 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation NV43 [GeForce 6600 LE] (rev a2)
**02:00.0 Ethernet controller: Intel Corporation 82573V Gigabit Ethernet Controller (Copper) (rev 03)**
07:05.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)
neil@neil-ubuntu:~/Desktop/ioatdma-2.15$

So is it just a matter of compiling and installing the driver from the sourceforge site

---

### Post by neilrudden on 2008-02-18
bump

---

### Post by Zarathu on 2008-02-18
```
ifconfig eth0 up
```

That's my only guess. :/

---

### Post by neilrudden on 2008-02-22
running ifconfig eth0 up

shows

eth0: ERROR while getting interface flags: No such device

the ethernet card does not seem to have been 'linked' to be a network device?

---

### Post by Iowan on 2008-02-22
Try just **ifconfig** to get information.  Also, post **/etc/network/interfaces**.  Should look something like:```
auto lo
iface lo inet loopback

auto eth0
#iface eth0 inet dhcp

auto eth1
#iface eth1 inet dhcp

auto eth2
#iface eth2 inet dhcp

auto ath0
#iface ath0 inet dhcp

auto wlan0
#iface wlan0 inet dhcp


iface eth0 inet dhcp

```
The **auto eth0** should be there.  An uncommented line about **iface eth0** should be there, too... verbiage will depend on whether you set up "Wired connection" for DHCP, static, or Local zeroconf (I'm not really familiar with this one).

---

### Post by neilrudden on 2008-02-23
ifconfig

auto lo
iface lo inet loopback

/etc/network/interfdaces

lo             Link encap: Local Loopback
                inet addr 127.0.0.1 Mask 255.0.0.0
                

nothing about intel network

---

### Post by Iowan on 2008-02-23
Under System>Administration>Network... is "Wired connection" checked? If so, highlight it (click on it), then click "Properties" How is card set up?

---

### Post by neilrudden on 2008-02-24
I think that is my main problem is that the connection is not seem by the os.

Under Administration/Network there is no eth0 connection.

Thank you for al responses so far

NEil

---

