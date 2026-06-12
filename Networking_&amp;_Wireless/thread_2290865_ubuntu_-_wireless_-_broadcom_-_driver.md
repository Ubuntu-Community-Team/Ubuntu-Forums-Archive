---
title: "ubuntu - wireless - broadcom - driver"
date: 2015-08-16
forum: Networking &amp; Wireless
---

### Post by nasir-sepehri on 2015-08-16
Hi
My wireless device model is** 06:00.0 Network controller [0280]: Broadcom Corporation BCM4321 802.11a/b/g/n [14e4:4328] (rev 03)**.
Ubuntu recommend install **bcmwl-kernel-source** in "*Additional drivers*" , but it's not work with new access point. so I search it and I found a solution for it . I install **b43-fwcutter &  firmware-b43-installer**. It's work but sometimes disconnect and never connect again and I should reset my laptop to connect again. 
what do i do?
thanks.

---

### Post by Bucky Ball on 2015-08-16
Welcome. Perhaps post the output of this from your terminal:

```
sudo lshw -C network
```

Also, follow the instructions from here:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#A12.04_.28Precise_Pangolin.29](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#A12.04_.28Precise_Pangolin.29)

---

### Post by nasir-sepehri on 2015-08-16
sudo lshw -C network
  *-network               
       description: Network controller
       product: BCM4321 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:19 memory:f4000000-f4003fff memory:fc000000-fc0fffff
  *-network
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: eth0
       version: 02
       serial: 00:21:70:a6:bc:1b
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=172.16.179.108 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:28 ioport:5000(size=256) memory:f8610000-f8610fff memory:f8600000-f860ffff memory:c0000000-c000ffff

---

### Post by Bucky Ball on 2015-08-16
Did you follow the instructions at the link I gave? Top of the page for 12.04 LTS [HERE]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#A12.04_.28Precise_Pangolin.29"). Works fine on newer releases. You need to get online with an ethernet cable before doing these steps. If you can't get online with a cable follow the instructions directly underneath headed 'STA - No Internet access'.

Good luck and let us know how you go. At the moment you have no driver installed for that wireless device, but it is recognised fine. :)

(PS: Please use code tags for terminal output. See the last link in my signature.)

---

### Post by nasir-sepehri on 2015-08-18
First of all, let me thank you for your attention . I read your page that you refer to it , and don't exist new thing. :(( 
I think the problem is my Kernel version(3.19.0-26-generic).
because when I install bcmwl-kernel-source from terminal , the result was :
0 upgraded, 1 newly installed, 0 to remove and 2 not upgraded.
Need to get 0 B/1,509 kB of archives.
After this operation, 8,038 kB of additional disk space will be used.
Selecting previously unselected package bcmwl-kernel-source.
(Reading database ... 251563 files and directories currently installed.)
Preparing to unpack .../bcmwl-kernel-source_6.30.223.248+bdcom-0ubuntu2_amd64.deb ...
Unpacking bcmwl-kernel-source (6.30.223.248+bdcom-0ubuntu2) ...
Setting up bcmwl-kernel-source (6.30.223.248+bdcom-0ubuntu2) ...
Loading new bcmwl-6.30.223.248+bdcom DKMS files...
First Installation: checking all kernels...
Building only for 3.19.0-26-generic
Building for architecture x86_64
Building initial module for 3.19.0-26-generic
Done.

wl:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.19.0-26-generic/updates/dkms/

depmod.........

DKMS: install completed.
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools (0.103ubuntu15) ...
update-initramfs: Generating /boot/initrd.img-3.19.0-26-generic


Do you think that I should install Ubuntu 14.04 ????

---

### Post by Bucky Ball on 2015-08-18
Looks fine to me. Complete all the instructions. You've included the output of one. Have you followed what's below that on the link and tested?

---

### Post by nasir-sepehri on 2015-08-21
Hi . 
I installed **firmware-b43-installer** **.**It's work but if access point refresh , my wireless do not connect again. and I should reset my laptop.[COLOR=#333333][FONT=UbuntuMono]
[/FONT][/COLOR]my access point model is AIR-CAP1702I-E-K9 (cisco Aironet 1700 series 802.11ac Dual Band Access point)

 I installed **bcmwl-kernel-source** when used cisco Airenet 1130AG access point , and I have not any problems .

---

### Post by Bucky Ball on 2015-08-21
Please post the output of the command I gave earlier again and we'll see what is now in there:

```
sudo lshw -C network
```

Access point doesn't make a difference. As long as it's on, online, and sending a signal, all is well. If you're not connecting to it, or connecting poorly, configuration or hardware issue locally.

---

### Post by nasir-sepehri on 2015-08-21
$ sudo lshw -C network
 
  *-network               
       description: Network controller
       product: BCM4321 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:19 memory:f4000000-f4003fff memory:fc000000-fc0fffff
  *-network
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: eth0
       version: 02
       serial: 00:21:70:a6:bc:1b
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:28 ioport:5000(size=256) memory:f8610000-f8610fff memory:f8600000-f860ffff memory:c0000000-c000ffff
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:22:69:12:e0:01
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=3.19.0-26-generic firmware=666.2 ip=172.31.60.0 link=yes multicast=yes wireless=IEEE 802.11abg

---

