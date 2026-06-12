---
title: "Wired Network"
date: 2020-03-23
forum: Networking &amp; Wireless
---

### Post by shakeypuss on 2020-03-23
My wireless card is working but I cannot get my wired connection working. Here is a partial output of lshw -C network:
*-network UNCLAIMED
       description: Ethernet Controller
       product: Qualcomm Atheros
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:03:00.0
       version 10
       width: 64 bits
       clock 33MHz
       capabilities: pm pciexpress msi msix bus_master cap_list
       configuration : latency=0
       resources: memory:92c00000-92c3ffff ioport:2000(Size=128)

How do I activate and set it to DHCP? It's currently plugged into a network.

---

### Post by chili555 on 2020-03-23
Unclaimed means that it lacks a working driver. Let's see why. Please run and post:

```
lspci -nnk | grep 0200 -A3
dmesg | grep ath
```Thanks.

---

### Post by shakeypuss on 2020-03-24
Thanks chili555; here's the output:
jian@manley-RNA-seq:~$ lspci -nnk | grep 0200 -A3
03:00.0 Ethernet controller [0200]: Qualcomm Atheros Device [1969:e0b1] (rev 10)
Subsystem: Micro-Star International Co., Ltd. [MSI] Device [1462:7a90]
04:00.0 Network controller [0280]: Qualcomm Atheros QCA6174 802.11ac Wireless Network Adapter [168c:003e] (rev 32)
Subsystem: Bigfoot Networks, Inc. Device [1a56:1535]

jian@manley-RNA-seq:~$ dmesg |grep ath
[    1.084193] Loaded X.509 cert 'Magrathea: Glacier signing key: df289f3b0cbf40ae3bfcbe5a73d072ed7648de5e'

---

### Post by chili555 on 2020-03-24
> Ethernet controller [0200]: Qualcomm Atheros Device [[COLOR="#FF0000"]1969:e0b1[/COLOR]] (rev 10)
Subsystem: Micro-Star International Co., Ltd. [MSI] Device [1462:7a90]The usual driver for this device is alx. Let's load it and see if there are any interesting messages, errors, etc.

```
sudo modprobe alx && dmesg | grep alx
```

---

### Post by shakeypuss on 2020-03-24
No output:
jian@manley-RNA-seq:~$ sudo modprobe alx && dmesg | grep alx
jian@manley-RNA-seq:~$

---

### Post by chili555 on 2020-03-24
> **shakeypuss said:**
> No output:
jian@manley-RNA-seq:~$ sudo modprobe alx && dmesg | grep alx
jian@manley-RNA-seq:~$That's weird.

I wonder why they always give me the hard problems to solve. Can't I get the occaisional softball, guys??

Let's dig deeper. We'll try to see what's going on on the PCI bus:

```
dmesg | grep 03:00
modinfo alx | grep E0B1

```That's E-**zero**-B-one; not a capital O.

---

### Post by shakeypuss on 2020-03-25
jian@manley-RNA-seq:~$ dmesg | grep 03:00
[    0.588062] pci 0000:03:00.0: [1969:e0b1] type 00 class 0x020000
[    0.588082] pci 0000:03:00.0: reg 0x10: [mem 0x92c00000-0x92c3ffff 64bit]
[    0.588092] pci 0000:03:00.0: reg 0x18: [io  0x2000-0x207f]
[    0.588182] pci 0000:03:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.588208] pci 0000:03:00.0: System wakeup disabled by ACPI
[    0.882251] pci 0000:03:00.0: Signaling PME through PCIe PME interrupt
jian@manley-RNA-seq:~$ modinfo alx | grep E0B1
jian@manley-RNA-seq:~$

---

### Post by chili555 on 2020-03-25
> 
jian@manley-RNA-seq:~$ modinfo alx | grep E0B1
jian@manley-RNA-seq:~$That means that the version of the driver alx in your system *doesn't* cover your exact device. Let's see:```
modinfo alx | grep file
lsb_release -d
```

---

### Post by shakeypuss on 2020-03-25
jian@manley-RNA-seq:~$ modinfo alx | grep file
filename:       /lib/modules/3.13.0-159-generic/kernel/drivers/net/ethernet/atheros/alx/alx.ko
jian@manley-RNA-seq:~$ lsb_release -d
Description:    Ubuntu 14.04.6 LTS

---

### Post by TheFu on 2020-03-25
> **shakeypuss said:**
> jian@manley-RNA-seq:~$ modinfo alx | grep file
filename:       /lib/modules/3.13.0-159-generic/kernel/drivers/net/ethernet/atheros/alx/alx.ko
jian@manley-RNA-seq:~$ lsb_release -d
Description:    Ubuntu 14.04.6 LTS

Support for 14.04.x ended about a year ago.  Move to 16.04 or better, **18.04**.
[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)  Of course, you could pay Canonical for ESM support, but most people find the cost isn't worth it due to all the other hassles they will see running a 6 yr old release.

Chilli - you get the hard ones due to your amazing ability to get to the answer so fast.

I had an alx NIC. It was a USB3-to-GigE adapter with 4 USB3 ports.  Perfect for a laptop that didn't have any RJ-45 ports.  After about 6 yrs, that device died and I got a $20 replacement which is used almost daily.

---

### Post by chili555 on 2020-03-25
> 
Support for 14.04.x ended about a year ago. Move to 16.04 or better, 18.04.
Yes, indeed! We are fairly confident that if you run a live version of 18.04 LTS, your ethernet will work immediately. If it does, then we recommend that you install it.

@TheFu Thank you for your very kind words.

---

