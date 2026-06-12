---
title: "Ubuntu 14.04 and Realtek 8169 no connectitivity"
date: 2014-08-28
forum: Networking &amp; Wireless
---

### Post by chad12 on 2014-08-28
I installed a fresh copy of Ubuntu on a Dell Optiplex 3020 with a Realtek 8111/8168/8411 Gigabit NIC. I initially blacklisted the 8169 and installed the r8168-8.035.00.tar.bz2 from Realtek's website. But after I rebooted my network card lost connectivity again. when I ran the ```
sudo lshw -C network
``` it said network unclaimed.
After all that frustraion I decided to virtualise the installation to test further, This is the out put from ```
sudo lshw -C network
``` command while in VMware.

```
 *-network               
       description: Ethernet interface
       product: 82545EM Gigabit Ethernet Controller (Copper)
       vendor: Intel Corporation
       physical id: 5
       bus info: pci@0000:02:05.0
       logical name: eth0
       version: 01
       serial: 00:0c:29:1e:4e:ff
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 66MHz
       capabilities: pm pcix bus_master cap_list rom ethernet physical logical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.21-k8-NAPI duplex=full ip=172.16.0.2 latency=0 link=yes mingnt=255 multicast=yes port=twisted pair speed=1Gbit/s
       resources: irq:19 memory:fd5c0000-fd5dffff memory:fdff0000-fdffffff ioport:2040(size=64) memory:e7b10000-e7b1ffff
```
It listed a different NIC from when it was bare-metal.

Please assist me.

---

### Post by chili555 on 2014-08-28
> It listed a different NIC from when it was bare-metal....and:> After all that frustraion I decided to virtualise the installation to test furtherI haven't the faintest idea how installing a virtual machine may assist in testing your ethernet. I'll be happy to assist you to troubleshoot on the host. Is it running Ubuntu? I suggest you run your diagnostics on the host machine and we'll proceed.

---

### Post by chad12 on 2014-08-28
I really just wanted Ubuntu as a VM. I installed it bare-metal to see if I could get the NIC working. I am running Windows 7 as the Host. I am not getting any conenctivity on the Guest (Ubuntu 14.04).

---

### Post by chili555 on 2014-08-28
Networking works a bit differently in virtual machines. I hope this will help. [https://www.virtualbox.org/manual/ch06.html](https://www.virtualbox.org/manual/ch06.html)

---

### Post by chad12 on 2014-08-29
The exact connectivity issue I was having when Ubuntu was bare metal is the same issue I am having now that its virtual. The NIC chipset, r8168 is problematic. It is now emaulated as a Intel [FONT=Ubuntu Mono, monospace][COLOR=#000000]82545EM Gigibit NIC. How do I get this connection of the Ethernet back up?[/COLOR][/FONT]

---

### Post by chili555 on 2014-08-29
I believe you'll need to fix the r8169 driver on the bare metal side. As the host is Win7, it is beyond the scope of this forum and my knowledge. I believe that, once the bare metal Realtek is working correctly, then, in the virtual machine, the emulation NIC will bridge to it and connect as expected.

---

### Post by chad12 on 2014-08-29
The exact connectivity issue I was having when Ubuntu was bare metal is the same issue I am having now that its virtual. The NIC chipset, r8168 is problematic. It is now emaulated as a Intel [FONT=Ubuntu Mono][COLOR=#000000]82545EM Gigibit NIC. How do I get this connection of the Ethernet back up?

[/COLOR][/FONT][FONT=Ubuntu Mono][COLOR=#000000]So the NIC just started back working on it's own. I decided to change the driver from r8169 to r8168. Blacklisted r8169 driver and installed the r8168-8.038.00.tar.bz2.
After using this command
[/COLOR][/FONT]```
sudo update-initramfs -u && cd ~/Desktop && tar xvf r8168-8.038.00.tar.bz2 && cd r8168-8.038.00 && sudo sh autorun.sh
```[FONT=Ubuntu Mono][COLOR=#000000]
the internet was still up and the network connection was good.
I then restarted and got this

```
[/COLOR][/FONT][FONT=Verdana]sudo lshw -C network[/FONT]
[FONT=Verdana][sudo] password for schooltool: [/FONT]
[FONT=Verdana]*-network UNCLAIMED [/FONT]
[FONT=Verdana]description: Ethernet controller[/FONT]
[FONT=Verdana]product: 82545EM Gigabit Ethernet Controller (Copper)[/FONT]
[FONT=Verdana]vendor: Intel Corporation[/FONT]
[FONT=Verdana]physical id: 5[/FONT]
[FONT=Verdana]bus info: pci@0000:02:05.0[/FONT]
[FONT=Verdana]version: 01[/FONT]
[FONT=Verdana]width: 64 bits[/FONT]
[FONT=Verdana]clock: 66MHz[/FONT]
[FONT=Verdana]capabilities: pm pcix cap_list[/FONT]
[FONT=Verdana]configuration: latency=0 mingnt=255[/FONT]
[FONT=Verdana]resources: memory:fd5c0000-fd5dffff memory:fdff0000-fdffffff ioport:2040(size=64) memory:e7b10000-e7b1ffff[/FONT]
[FONT=Verdana]schooltool@TRSRVST:~$[/FONT][FONT=Ubuntu Mono][COLOR=#000000]
```
[/COLOR][/FONT]

---

### Post by chili555 on 2014-08-29
```
*-network UNCLAIMED 
description: Ethernet controller
product: 82545EM Gigabit Ethernet Controller (Copper)
vendor: Intel Corporation
```I believe, from your previous paste, that the driver is *e1000*. Does everything come to life if you load the driver?```
sudo modprobe e1000
```If so, although, as I said, I am not familiar with VMs, you could add it to /etc/modules to get it to load on boot:```
sudo -i
echo e1000  >>  /etc/modules
exit
```

---

### Post by chad12 on 2014-08-29
OK Chili, I have reinstalled the Ubuntu 14.04 bare metal on a Dell Optiplex 3020 with r8369 driver installed and no internet or network connectivity. What do you want me to do next?

---

### Post by chili555 on 2014-08-29
> **chad12 said:**
> OK Chili, I have reinstalled the Ubuntu 14.04 bare metal on a Dell Optiplex 3020 with r8369 driver installed and no internet or network connectivity. What do you want me to do next?I suggest you compile the r8168-8.038.00 package as before.

---

### Post by chad12 on 2014-08-29
This is output from fresh install:

```
tranquillity@TRVMHOST01:~$ sudo lshw -C network[sudo] password for tranquillity: 
  *-network               
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 0c
       serial: f8:bc:12:75:16:87
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8168g-2_0.0.1 02/06/13 ip=172.16.0.7 latency=0 link=yes multicast=yes port=MII speed=1Gbit/s
       resources: irq:44 ioport:e000(size=256) memory:f7c00000-f7c00fff memory:f0000000-f0003fff
tranquillity@TRVMHOST01:~$ 
```

So I blacklisted the r6189 and installed the new driver, here is the output:

```
tranquillity@TRVMHOST01:~$ sudo update-initramfs -u && cd ~/Desktop && tar xvf r8168-8.038.00.tar.bz2 && cd r8168-8.038.00 && sudo sh autorun.shupdate-initramfs: Generating /boot/initrd.img-3.13.0-32-generic
r8168-8.038.00/
r8168-8.038.00/autorun.sh
r8168-8.038.00/Makefile
r8168-8.038.00/README
r8168-8.038.00/src/
r8168-8.038.00/src/Makefile
r8168-8.038.00/src/Makefile_linux24x
r8168-8.038.00/src/r8168.h
r8168-8.038.00/src/r8168_asf.c
r8168-8.038.00/src/r8168_asf.h
r8168-8.038.00/src/r8168_dash.h
r8168-8.038.00/src/r8168_n.c
r8168-8.038.00/src/rtltool.c
r8168-8.038.00/src/rtltool.h
r8168-8.038.00/src/rtl_eeprom.c
r8168-8.038.00/src/rtl_eeprom.h


Check old driver and unload it.
rmmod r8169
Build the module and install
Can't read private key
Backup r8169.ko
rename r8169.ko to r8169.bak
DEPMOD 3.13.0-32-generic
load module r8168
Updating initramfs. Please wait.
update-initramfs: Generating /boot/initrd.img-3.13.0-32-generic
Completed.
tranquillity@TRVMHOST01:~/Desktop/r8168-8.038.00$
```

After this finished I rebooted and ran the: ```
sudo lshw -C network
```
This is the output for it:

```
tranquillity@TRVMHOST01:~$ sudo lshw -C network[sudo] password for tranquillity: 
  *-network               
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 0c
       serial: f8:bc:12:75:16:87
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8168 driverversion=8.038.00-NAPI duplex=full ip=172.16.0.7 latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
       resources: irq:43 ioport:e000(size=256) memory:f7c00000-f7c00fff memory:f0000000-f0003fff
tranquillity@TRVMHOST01:~$
```

I can't ping the machine or get internet on it.

Edit: After rebooting I couldn't ping for about 5 mins then the ping jumped to life. Restarted again and pinged. Request timed out for exactly 6 mins and then a response came back. Its weird. So after install of r8168 the machines is accessible and can be pinged but only after 6 mins.

Tell me your thoughts.

---

### Post by chili555 on 2014-08-29
> ip=172.16.0.7You have an IP address. Does that agree with what you'd expect to see from other computers? What does this tell us?```
nm-tool
dmesg | grep -e eth0 -e r816
```Thanks.

---

### Post by chad12 on 2014-08-29
That IP is actually a static IP as this machine is a server that will be hosting virtual apps for the school.

I ran the command and it produced this:

```
tranquillity@TRVMHOST01:~$ nm-tool

NetworkManager Tool

State: connected (global)

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            r8168
  State:             connected
  Default:           yes
  HW Address:        F8:BC:12:75:16:87

  Capabilities:
    Carrier Detect:  yes
    Speed:           1000 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         172.16.0.7
    Prefix:          22 (255.255.252.0)
    Gateway:         172.16.0.1

    DNS:             172.16.0.4
    DNS:             172.16.0.5
```


```
tranquillity@TRVMHOST01:~$ dmesg | grep -e eth0 -e r816
[    0.632832] r8168: module verification failed: signature and/or  required key missing - tainting kernel
[    0.633104] r8168 Gigabit Ethernet driver 8.038.00-NAPI loaded
[    0.633228] r8168 0000:02:00.0: irq 43 for MSI/MSI-X
[    0.647393] r8168: This product is covered by one or more of the following patents: US6,570,884, US6,115,776, and US6,327,625.
[    0.647398] r8168  Copyright (C) 2013  Realtek NIC software team <nicfae@realtek.com> 
[    6.158119] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[    9.778650] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[    9.778783] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   12.790124] r8168: eth0: link up
[   12.790156] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
tranquillity@TRVMHOST01:~$
```

Your thoughts?

---

### Post by chili555 on 2014-08-29
> Your thoughts?You have an IP address, Network Manager says you are connected, although I am a bit suspicious about some of the settings. Are xx.4 and xx.5 actually DNS nameservers or...? Are they both pingable?

Why did you specify a netmask of 255.255.255.[COLOR="#FF0000"]252[/COLOR].0?

Nothing in your *dmesg* is in the least remarkable.

---

