---
title: "Strange Internet Problem"
date: 2007-03-25
forum: Networking &amp; Wireless
---

### Post by colsandurz on 2007-03-25
Hi,

I'm dual booting windows 32 bit and ubuntu 6.11 64 bit.  Whenever I boot into windows and use the internet and boot back into ubuntu my internet connection completely breaks down.  The only thing I can successfully ping is localhost - I can't connect to anything else.

I made a post on the situation last night 
[http://www.ubuntuforums.org/showthread.php?t=392706](http://www.ubuntuforums.org/showthread.php?t=392706)

Here's some of my hardware
AMD Turion MT-40 2.2 GHz
Realtek RTL8168/8111 PCI-E Gigabit Ethernet NIC 
My computer is a MSI MS-1039 

The one idea I have is to use my wired connection for windows and wireless for ubuntu, but thats really just avoiding the problem instead of fixing it.

Can anyone tell how to fix this in either ubuntu or windows so both connections just work??
Thanks

---

### Post by tgalati4 on 2007-03-25
When you reboot, do you do a complete power down?  Sometimes the ethernet card has buffered memory to remember things like gateways and authentication packets that don't get cleared with a simple, warm, reboot.

If no change, then try booting with the live CD to see if you can see the network.  There may be a subtle problem with your installation.  If it works with the live CD, then you can start to narrow down the installed components of your Ubuntu distro.  Using synaptic to remove and then reinstall network components and drivers may give you a fresh start.

It's also possible that your school's MAC authentication uses a more sophisticated technique to determine who is at the other end.  Perhaps is sends a windows service ping to gather more information--(like your processor serial number).

Can you establish a connection under Ubuntu first and then connect under Windows?  I would dig into the details of the authentication process.

Good luck.

---

### Post by colsandurz on 2007-03-25
Well, I shut off my computer, waited a moment, then turned it back on.  The problem persisted.  Then I shut off my computer and unplugged the power supply and battery.  It worked!

Thank you for the insight.

---

### Post by Mr. C. on 2007-03-25
> **tgalati4 said:**
> When you reboot, do you do a complete power down?  Sometimes the ethernet card has buffered memory to remember things like gateways and authentication packets that don't get cleared with a simple, warm, reboot.

If no change, then try booting with the live CD to see if you can see the network.  There may be a subtle problem with your installation.  If it works with the live CD, then you can start to narrow down the installed components of your Ubuntu distro.  Using synaptic to remove and then reinstall network components and drivers may give you a fresh start.

It's also possible that your school's MAC authentication uses a more sophisticated technique to determine who is at the other end.  Perhaps is sends a windows service ping to gather more information--(like your processor serial number).

... I would dig into the details of the authentication process.

This is nonsense.  All IP settings are configured during system bring up, and are lost on power down.  Nothing is retained during either warm or cold boot.

This is not Windows - random installations and reconfigurations is not necessary.

No processor serial number is being transmitted in ping packets, or any other TCP/IP packets.

Please don't spread misinformation.

colsandurz - Can you clarify something?  You say you have wired and wireless; but in your referenced post, only one interface (eth0) is shown.

Please show output from:

```
ifconfig -a
cat /etc/network/interfaces
cat /etc/resolv.conf
lspci
lspci -n
```

MrC

---

### Post by colsandurz on 2007-03-27
Well, my I ahve a wireless card it's just not set up in any way (in linux).  I meant I could set it up.

I have a question though, the problem never happens when I power down from windows and then take out the battery and power cord.  

Here's the output from that command

```


devin@dkelly:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:16:17:4F:9C:35  
          inet addr:130.215.230.181  Bcast:130.215.231.255  Mask:255.255.254.0
          inet6 addr: 2002:82d7:a97c:4:216:17ff:fe4f:9c35/64 Scope:Global
          inet6 addr: fec0::4:216:17ff:fe4f:9c35/64 Scope:Site
          inet6 addr: 2002:82d7:e68d:4:216:17ff:fe4f:9c35/64 Scope:Global
          inet6 addr: fe80::216:17ff:fe4f:9c35/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:20006 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3839 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4390908 (4.1 MiB)  TX bytes:658023 (642.6 KiB)
          Interrupt:225 Base address:0xa800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

ra0       Link encap:Ethernet  HWaddr 00:13:D3:75:D8:62  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:217 Base address:0x8000 

sit0      Link encap:IPv6-in-IPv4  
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)


devin@dkelly:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:16:17:4F:9C:35  
          inet addr:130.215.230.181  Bcast:130.215.231.255  Mask:255.255.254.0
          inet6 addr: 2002:82d7:a97c:4:216:17ff:fe4f:9c35/64 Scope:Global
          inet6 addr: fec0::4:216:17ff:fe4f:9c35/64 Scope:Site
          inet6 addr: 2002:82d7:e68d:4:216:17ff:fe4f:9c35/64 Scope:Global
          inet6 addr: fe80::216:17ff:fe4f:9c35/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:20006 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3839 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4390908 (4.1 MiB)  TX bytes:658023 (642.6 KiB)
          Interrupt:225 Base address:0xa800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

ra0       Link encap:Ethernet  HWaddr 00:13:D3:75:D8:62  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:217 Base address:0x8000 

sit0      Link encap:IPv6-in-IPv4  
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

devin@dkelly:~$ cat /etc/resolv.conf
search res.wpi.net
nameserver 130.215.39.18
nameserver 130.215.32.18
nameserver 130.215.39.82
nameserver 130.215.36.18

devin@dkelly:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 01)
00:02.0 PCI bridge: ATI Technologies Inc RS480 PCI-X Root Port
00:04.0 PCI bridge: ATI Technologies Inc Unknown device 5a36
00:05.0 PCI bridge: ATI Technologies Inc Unknown device 5a37
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 82)
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller ATI (rev 80)
00:14.2 Audio device: ATI Technologies Inc Unknown device 437b (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: ATI Technologies Inc Unknown device 71c5
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. Unknown device 8168 (rev 01)
05:04.0 CardBus bridge: O2 Micro, Inc. OZ711MP1/MS1 MemoryCardBus Controller (rev 21)
05:04.2 Class 0805: O2 Micro, Inc. Unknown device 7120 (rev 01)
05:04.3 Bridge: O2 Micro, Inc. Unknown device 7130 (rev 01)
05:04.4 FireWire (IEEE 1394): O2 Micro, Inc. Unknown device 00f7 (rev 02)
05:09.0 Network controller: RaLink RT2500 802.11g Cardbus/mini-PCI (rev 01)
06:00.0 Multimedia audio controller: Creative Labs SB0400 Audigy2 Value


devin@dkelly:~$ lspci -n
00:00.0 0600: 1002:5950 (rev 01)
00:02.0 0604: 1002:5a34
00:04.0 0604: 1002:5a36
00:05.0 0604: 1002:5a37
00:13.0 0c03: 1002:4374 (rev 80)
00:13.1 0c03: 1002:4375 (rev 80)
00:13.2 0c03: 1002:4373 (rev 80)
00:14.0 0c05: 1002:4372 (rev 82)
00:14.1 0101: 1002:4376 (rev 80)
00:14.2 0403: 1002:437b (rev 01)
00:14.3 0601: 1002:4377 (rev 80)
00:14.4 0604: 1002:4371 (rev 80)
00:18.0 0600: 1022:1100
00:18.1 0600: 1022:1101
00:18.2 0600: 1022:1102
00:18.3 0600: 1022:1103
01:00.0 0300: 1002:71c5
04:00.0 0200: 10ec:8168 (rev 01)
05:04.0 0607: 1217:7134 (rev 21)
05:04.2 0805: 1217:7120 (rev 01)
05:04.3 0680: 1217:7130 (rev 01)
05:04.4 0c00: 1217:00f7 (rev 02)
05:09.0 0280: 1814:0201 (rev 01)
06:00.0 0401: 1102:0008



```

---

### Post by Mr. C. on 2007-03-27
Here's the problem:

```
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. **Unknown device 8168** (rev 01)
```

The driver you have does not recognize this device.  This person had the same device and same problem:

[http://ubuntuforums.org/showthread.php?t=385582&page=2&highlight=mrc+8168](http://ubuntuforums.org/showthread.php?t=385582&page=2&highlight=mrc+8168)

and there are other similar posts.  Search the forums for 8168.  You will need an updated driver from Realtek, or have to use your other NIC.

MrC

---

