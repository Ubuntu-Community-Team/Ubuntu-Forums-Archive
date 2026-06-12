---
title: "Wired and wireless not working"
date: 2014-06-05
forum: Networking &amp; Wireless
---

### Post by Nick_Otero on 2014-06-05
Hey everyone,

I inherited a board and it cannot connect to wired or wireless internet.  It is running Ubuntu 11.04.  I have spent all day trying to find a solution but am having no luck.  I am hoping someone here might be able to help.  Here is some info I have gotten while looking at other suggestions:

```
ifconfig:


eth0      Link encap:Ethernet  HWaddr 00:25:22:fa:83:07  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:43 


eth2      Link encap:Ethernet  HWaddr 00:0e:c6:88:f6:f8  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:94 (94.0 B)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:627224 errors:0 dropped:0 overruns:0 frame:0
          TX packets:627224 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:64549313 (64.5 MB)  TX bytes:64549313 (64.5 MB)


cat /etc/network/interfaces:


auto lo
iface lo inet loopback


auto eth0
iface eth0 inet dhcp




cat /etc/NetworkManager/NetworkManager.conf:


# This file is installed into /etc/NetworkManager, and is loaded by 
# NetworkManager by default.  To override, specify: '--config file' 
# during NM startup.  This can be done by appending to DAEMON_OPTS in 
# the file:
#
# /etc/default/NetworkManager
#


[main]
plugins=ifupdown,keyfile


no-auto-default=00:25:22:fa:83:07,


[ifupdown]
managed=true




sudo lshw -C network:


  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 06
       serial: 00:25:22:fa:83:07
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:43 ioport:e000(size=256) memory:d0004000-d0004fff memory:d0000000-d0003fff
  *-network
       description: Ethernet interface
       physical id: 1
       logical name: eth2
       serial: 00:0e:c6:88:f6:f8
       size: 10Mbit/s
       capacity: 1Gbit/s
       capabilities: ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=asix driverversion=22-Aug-2005 duplex=half firmware=ASIX AX88178 USB 2.0 Ethernet link=no multicast=yes port=MII speed=10Mbit/s


lspci:


00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB Controller: Intel Corporation 6 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 6 Series Chipset Family High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 1 (rev b5)
00:1c.3 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 4 (rev b5)
00:1c.5 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 6 (rev b5)
00:1d.0 USB Controller: Intel Corporation 6 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation 6 Series Chipset Family LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 6 Series Chipset Family 6 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 6 Series Chipset Family SMBus Controller (rev 05)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
03:00.0 USB Controller: Device 1b21:1042

```

Thanks in advance for your help!

---

### Post by grahammechanical on 2014-06-05
In trying to fix this did you install another network manager? This is what I see on my OS when I run 

```
cat /etc/network/interfaces
```
> 
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback




Anything else in that file will prevent the Ubuntu Network Manager from working. You have some additional lines in your interfaces file. Try removing the additional lines and rebooting and then use Network manager to connect to the router. What else?

ifconfig shows two ethernet devices (eth0 and eth1) but no wirelss device (wlan0). Are you sure that motherboard has a wireless adapter? Is it disabled in the BIOS? We want ifconfig to show UP BROADCAST RUNNING MULTICAST to prove that each adapter is connected to the router. You do not have RUNNING.

lshw -C network shows that there is a driver for both you ethernet adapters (physical id: 0 driver=r8169; physical id: 1 driver=asix) and that is a sign that your ethernet adapters are recognised by the OS. But there is no mention of a wireless adapter. This is the kind of thing that you should be seeing

> *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@1:3
       logical name: wlan0
       serial: 00:15:af:0e:9b:e0
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rtl8187 driverversion=3.15.0-5-generic firmware=N/A link=no multicast=yes wireless=IEEE 802.11bg


Notice, that there is a driver for my wireless adapter = rtl8187.

Regards.

---

### Post by Nick_Otero on 2014-06-06
> **grahammechanical said:**
> In trying to fix this did you install another network manager? This is what I see on my OS when I run 



I put the extra line in according to a post I saw in another thread about trying to fix the problem.  I will remove it.

> **grahammechanical said:**
> 
ifconfig shows two ethernet devices (eth0 and eth1) but no wirelss device (wlan0). Are you sure that motherboard has a wireless adapter? Is it disabled in the BIOS? We want ifconfig to show UP BROADCAST RUNNING MULTICAST to prove that each adapter is connected to the router. You do not have RUNNING.


I believe it does have a wireless adapter, because the students who used it before me were able to set up a private wireless network.  I haven't been able to check because the board is sealed in an everything-proof case, but I am going to try and open it up today.  I'll see if the adapter was taken out or not.

Thanks for your advice!

---

### Post by gordintoronto on 2014-06-06
11.04 is not currently supported, which might make solving the problem impossible.

Is it possible that the students were using a USB wireless adapter?

---

### Post by varunendra on 2014-06-07
Even if it had a wireless adapter, it is either broken or disconnected. Nothing can be done if the OS doesn't 'see' it. Check your BIOS - is there anything about wireless adapter or its settings?

For Ethernet, try this -
```
sudo mii-tool -F 100baseTx-FD eth0
```
If it goes fine, you should have a working link between the card and the router (assuming you are connecting via 'eth0'), rest depends on logical configuration (DHCP, IP addressing etc.). If it returns error, we may have to install 'ethtool' somehow. In case of error, what does this return -
```
apt-get install --print-uris ethtool
```??

Also, please show us the output of -
```
cat /etc/udev/rules.d/70-persistent-net.rules
```

---

### Post by Nick_Otero on 2014-06-07
Hey guys,

Thanks a lot for your help, luckily a grad student worked some magic and got everything up and running.  Thanks again!

---

### Post by varunendra on 2014-06-07
Please mark the thread as [SOLVED] now that it is. :)
(use "Thread Tools" link above the top post)

---

