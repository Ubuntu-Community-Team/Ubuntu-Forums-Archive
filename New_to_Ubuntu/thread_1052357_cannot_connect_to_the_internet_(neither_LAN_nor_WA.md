---
title: "cannot connect to the internet (neither LAN nor WAN) help :\"
date: 2009-01-27
forum: New to Ubuntu
---

### Post by dmurat on 2009-01-27
hi there
i just completed a fresh install of ubuntu 8.10 to my desktop computer but im not able to access the local page of my router. i cant even open google =)

here are the resutls for ifconfig, iwconfig and lspci one after the other. thought it d help you to help =)

```
dmurat@dmurat-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:21:85:c8:e1:ea  
          UP BROADCAST RUNNING MULTICAST  MTU:64  Metric:1
          RX packets:758 errors:0 dropped:2678888950 overruns:0 frame:0
          TX packets:11 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:83070 (83.0 KB)  TX bytes:2923 (2.9 KB)
          Interrupt:221 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:486 errors:0 dropped:0 overruns:0 frame:0
          TX packets:486 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:30448 (30.4 KB)  TX bytes:30448 (30.4 KB)

dmurat@dmurat-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

dmurat@dmurat-desktop:~$ lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:02.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (ext gfx port 0)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [IDE mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] Link Control
01:00.0 VGA compatible controller: ATI Technologies Inc RV770 [Radeon HD 4850]
01:00.1 Audio device: ATI Technologies Inc HD48x0 audio
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
```

thanks

---

### Post by dmurat on 2009-01-28
/bump
i d appreciate any suggestions... just need help to get away from vista and start using ubuntu once again..

*btw i connect to the internet through an ethernet cable with adsl. (onboard ethernet)

---

### Post by ellgor on 2009-01-28
Hi,

Try switching the modem off for about a minute then restart, sometimes a new setting is not recognised until the equivalent of a reboot happens, found this out after six months of trial and error and nearly adjusting things with a hammer.

Regards, Ellgor.

---

### Post by dmurat on 2009-01-28
thanks ellgor but i tried and it didnt work unfortunately :\ do you have another suggestion?

---

### Post by cariboo on 2009-01-28
There two things you need to check, open a Applications-->Accessories-->Terminal and type:

```
sudo lshw -C network
```

the above command will list the details of your network cards and tell us if there is a driver loaded. If there is a driver loaded, click on Network Manager and click edit connections, click the dsl tab and then click the add button, answer  the questions, and should have a network connection.

Jim

---

### Post by dmurat on 2009-02-04
> **cariboo907 said:**
> There two things you need to check, open a Applications-->Accessories-->Terminal and type:

```
sudo lshw -C network
```

the above command will list the details of your network cards and tell us if there is a driver loaded. If there is a driver loaded, click on Network Manager and click edit connections, click the dsl tab and then click the add button, answer  the questions, and should have a network connection.

Jim

here is the output of the above command - i dont know if a driver is loaded but it can see "Realtek" but says: Network: disabled

```
:~$ sudo lshw -C network
[sudo] password for dmurat: 
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:21:85:c8:e1:ea
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full latency=0 link=yes module=r8169 multicast=yes port=twisted pair speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 5e:01:3e:80:6d:a2
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes


```

what can i do now? i still cant connect to the internet

---

### Post by dmurat on 2009-02-07
noone can help? :\

---

### Post by issih on 2009-02-07
Just to clarify how things are set up here...

You have a router/adsl modem that you connect to the computer via a network cable?

If that is right then the only thing we care about here is the eth0 interface. (lo is the loopback which is necessary but irrelevant here and the pan0 is probably a bluetooth connection, so it being disabled is not a problem).

The results of your ifconfig and lshw suggest that the network interface is being recognised by ubuntu and should be functional. You do not however have an IP address assigned to it. This suggests that you either have a problem with the dhcp server in your router not assigning an ip address, or your set up uses static ip's. 

Either way it is probably easiest to try setting a static ip to see if that helps. So right click on the network icon and edit the connection and add a static ip such that it is the same address as your router/adsl modem but with the final digit of the last of the quartet of numbers is incremented by one, e.g. 192.168.0.1 becomes 192.168.0.2.

Once a static IP is assigned see if you can ping the router and access the internet.

Hope that helps

---

### Post by Lostin60's on 2009-02-07
> **dmurat said:**
> /bump
i d appreciate any suggestions... just need help to get away from vista and start using ubuntu once again..

*btw i connect to the internet through an ethernet cable with adsl. (onboard ethernet)

Try right clicking your internet icon>edir connections>DSL Highlight your connection, click edit. You will see what you have vs what you need. IP, Mac addy, etc. You can post a screenshot. Either I, or someone will try to help from there.
[COLOR="White"]aa[/COLOR]

---

### Post by ugm6hr on 2009-02-07
[https://bugs.launchpad.net/ubuntu/+bug/208012](https://bugs.launchpad.net/ubuntu/+bug/208012)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/221499](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/221499)

Looks like your LAN card driver is being loaded incorrectly, and the correct driver is not included in the Hardy kernel.

So you have to manually download and install the driver, and then remove the default (incorrect) one.

---

