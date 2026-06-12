---
title: "Cannot connect to internet (ubuntu)"
date: 2011-08-31
forum: New to Ubuntu
---

### Post by Snowboi on 2011-08-31
My question has turned into a completely different question :S
now my computer can go on the internet on windows but cannot on ubuntu... I found out in my previous topic that i posted that it would not boot because i had turned off some startup services that allowed it to connect to the internet.

Please note that this is a university laptop it may be hardware restricted...

I can get ubuntu running on a live CD and fully functional except for the internet being unable to connect.

Link to my previous post (lots of commands done there please check before asking me to use terminal commands)
[http://ubuntuforums.org/showthread.php?t=1835843](http://ubuntuforums.org/showthread.php?t=1835843)

Please im really excited to get ubuntu on this laptop :D
thank you

---

### Post by cariboo on 2011-08-31
Could you post the output of:

```
sudo lshw -C network
```

in your next post. The above command will tell us if you network devices are detected, as well as what chipset they use, and whether a driver has been loaded.

---

### Post by Snowboi on 2011-08-31
> **cariboo907 said:**
> Could you post the output of:

```
sudo lshw -C network
```

in your next post. The above command will tell us if you network devices are detected, as well as what chipset they use, and whether a driver has been loaded.

```
 *-network UNCLAIMED     
       description: Ethernet controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       version: 04
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list
       configuration: latency=0
       resources: memory:f2600000-f261ffff memory:f262b000-f262bfff ioport:5080(size=32)
  *-network UNCLAIMED
       description: Network controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 34
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:f2500000-f2501fff
```

Hmm...

---

### Post by Snowboi on 2011-08-31
*bump*

---

### Post by Snowboi on 2011-09-01
problem still not solved :(

---

### Post by Redmage913 on 2011-09-01
Could you please list the output of ```
lspci
```
Or at least the network-related parts of it?

---

### Post by Snowboi on 2011-09-01
> **Redmage913 said:**
> Could you please list the output of ```
lspci
```
Or at least the network-related parts of it?

```
00:00.0 Host bridge: Intel Corporation Device 0104 (rev 09)
00:02.0 VGA compatible controller: Intel Corporation Device 0126 (rev 09)
00:16.0 Communication controller: Intel Corporation Cougar Point HECI Controller #1 (rev 04)
00:16.3 Serial controller: Intel Corporation Cougar Point KT Controller (rev 04)
00:19.0 Ethernet controller: Intel Corporation Device 1502 (rev 04)
00:1a.0 USB Controller: Intel Corporation Cougar Point USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation Cougar Point High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 1 (rev b4)
00:1c.1 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 2 (rev b4)
00:1c.3 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 4 (rev b4)
00:1c.4 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 5 (rev b4)
00:1d.0 USB Controller: Intel Corporation Cougar Point USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation Device 1c4f (rev 04)
00:1f.2 SATA controller: Intel Corporation Cougar Point 6 port SATA AHCI Controller (rev 04)
00:1f.3 SMBus: Intel Corporation Cougar Point SMBus Controller (rev 04)
03:00.0 Network controller: Intel Corporation Device 0085 (rev 34)
0d:00.0 System peripheral: Ricoh Co Ltd Device e823 (rev 05)
0d:00.3 FireWire (IEEE 1394): Ricoh Co Ltd Device e832 (rev 04)


```

---

### Post by Snowboi on 2011-09-02
bump =/

---

