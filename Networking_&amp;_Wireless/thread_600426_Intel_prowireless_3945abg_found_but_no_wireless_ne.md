---
title: "Intel pro/wireless 3945abg found but no wireless network"
date: 2007-11-02
forum: Networking &amp; Wireless
---

### Post by penguinfancier on 2007-11-02
Just installed 7.10 Ubuntu on a Vista machine and I cannot connect to my wireless network. 
Odd thing is though I ran the Live CD on my second laptop which has XP and the Intel pro/wireless 3945abg chip and it connected fine, but when I tried the same on my Vista laptop which has the same chip, nothing could be found. 
It tells me in restricted drivers that the Intel pro/wireless 3945abg is not free etc. and i have ticked the enable box. 

But alas when i go into network manager there is only wired or modem options, no wireless. It looks like the wireless is not starting on boot up with the OS. Or it is not recognised. I have tried the basics, new to linux etc. 

Any thoughts? Anyone know why it would work on my XP machine which has the same chip but not on my Vista machine?

(ps. if I cant get it working i will have to learn how to use Vista!)

---

### Post by Lambert on 2007-11-02
> **penguinfancier said:**
> Just installed 7.10 Ubuntu on a Vista machine and I cannot connect to my wireless network. 
Odd thing is though I ran the Live CD on my second laptop which has XP and the Intel pro/wireless 3945abg chip and it connected fine, but when I tried the same on my Vista laptop which has the same chip, nothing could be found. 
It tells me in restricted drivers that the Intel pro/wireless 3945abg is not free etc. and i have ticked the enable box. 

But alas when i go into network manager there is only wired or modem options, no wireless. It looks like the wireless is not starting on boot up with the OS. Or it is not recognised. I have tried the basics, new to linux etc. 

Any thoughts? Anyone know why it would work on my XP machine which has the same chip but not on my Vista machine?

(ps. if I cant get it working i will have to learn how to use Vista!)

Could be various reasons, such as diferent bus controllers or bridges which the keeps the kernel from reading the device properly and loading the driver.

Open up a terminal and type the following command.

[code]
sudo lshw -C network

lsmod | grep ipw

sudo iwconfig

sudo ifconfig
[/code

post outpur from these commands here.

---

### Post by penguinfancier on 2007-11-04
**Output:**

:~$ sudo lshw -C network

  *-network                      description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth0
       version: 01
       serial: 00:1b:fc:e2:26:34
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd 

autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=half latency=0 link=no 

module=r8169 multicast=yes port=twisted pair
  *-network
       description: Network controller
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=ipw3945 latency=0 module=ipw3945

------------------------------------------------------------------------


~$ lsmod | grep ipw

ipw3945               119840  1 
ieee80211              35656  1 ipw3945

-------------------------------------------------------------------------

~$ sudo iwconfig

lo        no wireless extensions.
eth0      no wireless extensions.

-------------------------------------------------------------------------


~$ sudo ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1B:FC:E2:26:34  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:16 Base address:0x8000 
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

---

### Post by geoff313 on 2007-11-12
Hello,

I am also experiencing a similar problem, except that my wireless networking was working at one point (using WPA encryption). However in the past few days my network card is not showing up in my available network interfaces (Under Administration->Network I see only Wired Connection and Modem Connection, where I previously had a Wireless Connection as well). The output for the same commands that you suggested penguinfancier run:

[B]
sudo lshw -C network[/B]

  *-network               
       description: Ethernet interfaced
       product: 88E8038 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 14
       serial: 00:1b:24:64:ec:67
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.18 duplex=full firmware=N/A ip=192.168.1.103 latency=0 link=yes module=sky2 multicast=yes port=twisted pair speed=100MB/s
  *-network
       description: Network controller
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=ipw3945 latency=0 module=ipw3945
[B]
lsmod | grep ipw[/B]

ipw3945               119840  1 
ieee80211              35656  1 ipw3945

[B]
sudo iwconfig[/B]

lo        no wireless extensions.

eth0      no wireless extensions.
[B]
sudo ifconfig[/B]

eth0      Link encap:Ethernet  HWaddr 00:1B:24:64:EC:67  
          inet addr:192.168.1.103  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:24ff:fe64:ec67/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5209 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5042 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4786977 (4.5 MB)  TX bytes:794671 (776.0 KB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)


As an aside my network card used to show up as eth1.

Thanks for all your help in this matter!!!

-geoff313

---

### Post by Lambert on 2007-11-13
You both are having the same issue, the device is reconized and a driver is loading but it's not assigning your device a logical name.

I'm not that familiar with how gutsy does this and how to fix this so this is a bump so hopefully someone else will see this and can answer.

One suggestion is to make sure the ipw3945d daemon is running. You can do this with

```

ps aux | grep ipw3945

```

If you get no output then it's not running.

---

### Post by geoff313 on 2007-11-13
Hello,

Just thought I would update you on my situation. I backtracked my steps to when my wireless was working, and I realized it stopped just after I installed the avant-window-manager. I uninstalled avant and rebooted Ubuntu and my wireless card was detected. I had noticed that after I installed avant it was taking much longer for X and Gnome to load, so perhaps there was some sort of conflict between the two.

@Lambert: I had previously done that, and indeed the daemon was running. Yet for some reason the module wasn't loading correctly (in my humble opinion)

Hopefully this helps someone,

-geoff313

---

