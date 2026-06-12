---
title: "Occasional drop in Internet"
date: 2008-09-14
forum: Networking &amp; Wireless
---

### Post by Codename46 on 2008-09-14
Ok so here's my problem.

This happened starting only a week ago.

I would be on my computer, and after a few hours, my internet connection just drops.

Pinging my router doesn't work. Pinging just about anything other than localhost and my own IP address doesn't work. I have a motherboard with 2 ethernet ports, and this problem would happen with both.

However if I goto System -> Administration -> Network, and disable/re-enable roaming mode, or just disabling roaming mode and using DHCP, it suddenly works again.

And then when it quits working again in a few hours, disabling DHCP and re-enabling roaming mode fixes it...temporarily again.

typing "sudo ifconfig eth0 up" in the console doesn't fix it

As far as I know this problem doesn't happen in Windows XP, since I dual-boot. I'm running Ubuntu 8.04

This is a really weird problem and I'll give a cookie to anyone who solves it.

---

### Post by pytheas22 on 2008-09-14
The next time a crash occurs, please immediately open a terminal and type:
```

dmesg | tail
ifconfig
lshw -C Network
lspci -nn
```

and post the output here.  That will hopefully provide a clue as to what's going on.

---

### Post by Codename46 on 2008-09-15
Ok I was able to type all that in the console while it was happening. Here:

> codename46@ARFCOM87:~$ dmesg | tail
[34872.311793] 0d8: 00000000 2e9b6cc6 2000004e // 00000000 2c9f30c6 2000004e // 00000000 2c9f34c6 2000004e // 00000000 2c9f38c6 2000004e
[34872.311796] 0dc: 00000000 1f66d93e 00000000 // 00000000 2eb2ad86 2000006b // 00000000 2c9f3cc6 2000004e // 00000000 3373a0c6 2000004e
[34872.311800] 0e0: 00000000 2ebf5cc6 2000004e // 00000000 336af0c6 2000004e // 00000000 3373acc6 2000004e // 00000000 339c4c02 20000058
[34872.311803] 0e4: 00000000 334b70c6 2000004e // 00000000 336af4c6 2000004e // 00000000 336af8c6 2000004e // 00000000 336afcc6 2000004e
[34872.311807] 0e8: 00000000 33a3c0c6 2000004e // 00000000 33a3c4c6 2000004e // 00000000 334b74c6 2000004e // 00000000 334b7cc6 2000004e
[34872.311810] 0ec: 00000000 334b78c6 2000004e // 00000000 319f30c6 2000004e // 00000000 319f34c6 2000004e // 00000000 319f38c6 2000004e
[34872.311814] 0f0: 00000000 319f3cc6 2000004e // 00000000 2e9d00c6 2000004e // 00000000 2e9d04c6 2000004e // 00000000 2e9d08c6 2000004e
[34872.311817] 0f4: 00000000 339c4402 2000006d // 00000000 2e9d0cc6 2000004e // 00000000 33a3c8c6 2000004e // 00000000 337980c6 2000004e
[34872.311821] 0f8: 00000000 337984c6 2000004e // 00000000 33a3ccc2 20000052 // 00000000 2eb080c6 2000004e // 00000000 2eb084c6 2000004e
[34872.311824] 0fc: 00000000 337988c6 2000004e // 00000000 2eb088c6 2000004e // 00000000 2eb08cc6 2000004e // 00000000 33798cc6 2000004e
codename46@ARFCOM87:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:15:58:69:d5:f0  
          inet addr:192.168.1.131  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::215:58ff:fe69:d5f0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3541222 errors:110 dropped:0 overruns:0 frame:110
          TX packets:2560622 errors:0 dropped:46 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3038938258 (2.8 GB)  TX bytes:1353706594 (1.2 GB)
          Interrupt:218 Base address:0x8000 

eth1      Link encap:Ethernet  HWaddr 00:15:58:69:d5:f1  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:219 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:10669 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10669 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:873460 (852.9 KB)  TX bytes:873460 (852.9 KB)

codename46@ARFCOM87:~$ lshw -C Network
WARNING: you should run this program as super-user.
PCI (sysfs)  
codename46@ARFCOM87:~$    
codename46@ARFCOM87:~$ sudo lshw -C Network
[sudo] password for codename46: 
codename46@ARFCOM87:~$ lspci -nn
00:00.0 RAM memory [0500]: nVidia Corporation C51 Host Bridge [10de:02f4] (rev a2)
00:00.1 RAM memory [0500]: nVidia Corporation C51 Memory Controller 0 [10de:02fa] (rev a2)
00:00.2 RAM memory [0500]: nVidia Corporation C51 Memory Controller 1 [10de:02fe] (rev a2)
00:00.3 RAM memory [0500]: nVidia Corporation C51 Memory Controller 5 [10de:02f8] (rev a2)
00:00.4 RAM memory [0500]: nVidia Corporation C51 Memory Controller 4 [10de:02f9] (rev a2)
00:00.5 RAM memory [0500]: nVidia Corporation C51 Host Bridge [10de:02ff] (rev a2)
00:00.6 RAM memory [0500]: nVidia Corporation C51 Memory Controller 3 [10de:027f] (rev a2)
00:00.7 RAM memory [0500]: nVidia Corporation C51 Memory Controller 2 [10de:027e] (rev a2)
00:04.0 PCI bridge [0604]: nVidia Corporation C51 PCI Express Bridge [10de:02fb] (rev a1)
00:08.0 RAM memory [0500]: nVidia Corporation MCP55 Memory Controller [10de:0369] (rev a1)
00:09.0 ISA bridge [0601]: nVidia Corporation MCP55 LPC Bridge [10de:0360] (rev a2)
00:09.1 SMBus [0c05]: nVidia Corporation MCP55 SMBus [10de:0368] (rev a2)
00:09.2 RAM memory [0500]: nVidia Corporation MCP55 Memory Controller [10de:036a] (rev a2)
00:0a.0 USB Controller [0c03]: nVidia Corporation MCP55 USB Controller [10de:036c] (rev a1)
00:0a.1 USB Controller [0c03]: nVidia Corporation MCP55 USB Controller [10de:036d] (rev a2)
00:0c.0 IDE interface [0101]: nVidia Corporation MCP55 IDE [10de:036e] (rev a1)
00:0d.0 IDE interface [0101]: nVidia Corporation MCP55 SATA Controller [10de:037f] (rev a2)
00:0d.1 IDE interface [0101]: nVidia Corporation MCP55 SATA Controller [10de:037f] (rev a2)
00:0d.2 IDE interface [0101]: nVidia Corporation MCP55 SATA Controller [10de:037f] (rev a2)
00:0e.0 PCI bridge [0604]: nVidia Corporation MCP55 PCI bridge [10de:0370] (rev a2)
00:10.0 Bridge [0680]: nVidia Corporation MCP55 Ethernet [10de:0373] (rev a2)
00:11.0 Bridge [0680]: nVidia Corporation MCP55 Ethernet [10de:0373] (rev a2)
00:12.0 PCI bridge [0604]: nVidia Corporation MCP55 PCI Express bridge [10de:0376] (rev a2)
00:16.0 PCI bridge [0604]: nVidia Corporation MCP55 PCI Express bridge [10de:0375] (rev a2)
00:17.0 PCI bridge [0604]: nVidia Corporation MCP55 PCI Express bridge [10de:0377] (rev a2)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
01:00.0 VGA compatible controller [0300]: nVidia Corporation GeForce 8800 GT [10de:0611] (rev a2)
02:08.0 FireWire (IEEE 1394) [0c00]: Texas Instruments TSB82AA2 IEEE-1394b Link Layer Controller [104c:8025] (rev 01)
02:0a.0 Multimedia audio controller [0401]: Creative Labs SB Audigy LS [1102:0007]


I appreciate the help.

---

### Post by Codename46 on 2008-09-15
Caught it again. I'm posting this again:

> codename46@ARFCOM87:~$ dmesg | tail
[48330.048534] 0d8: 00000000 334b0802 2000004d // 00000000 2ea98cd2 20000042 // 00000000 33b3b602 2000004e // 00000000 31a7acc6 2000004e
[48330.048537] 0dc: 00000000 2c8fe8c6 2000004e // 00000000 31a7a8c6 2000004e // 00000000 31a7a4c6 2000004e // 00000000 339e8202 2000006f
[48330.048541] 0e0: 00000000 339e8e02 2000006f // 00000000 339e8c02 2000006f // 00000000 3296ccc6 2000004e // 00000000 1f577cc6 2000004e
[48330.048545] 0e4: 00000000 1f5778c6 2000004e // 00000000 33fb9602 20000052 // 00000000 33fb9002 2000006f // 00000000 33fb9802 2000006f
[48330.048548] 0e8: 00000000 33fb9402 2000006f // 00000000 3363de02 20000059 // 00000000 334fa002 20000054 // 00000000 1f5770c6 2000004e
[48330.048552] 0ec: 00000000 33d1c802 2000006f // 00000000 1f5774c6 2000004e // 00000000 2e9a1cc6 2000004e // 00000000 2c9278c6 2000004e
[48330.048555] 0f0: 00000000 2c927cc6 2000004e // 00000000 2c9274ce 20000046 // 00000000 3296c4c6 2000004e // 00000000 2c9270c6 2000004e
[48330.048559] 0f4: 00000000 337340c6 2000004e // 00000000 337344c6 2000004e // 00000000 33734cc6 2000004e // 00000000 337348c6 2000004e
[48330.048562] 0f8: 00000000 2c9600c6 2000004e // 00000000 2eac14c6 2000004e // 00000000 2eac18c6 2000004e // 00000000 2eac10ce 20000046
[48330.048566] 0fc: 00000000 2eac1cce 20000046 // 00000000 33971c02 20000040 // 00000000 339ec802 20000040 // 00000000 2cb4c0da 20000040
codename46@ARFCOM87:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:15:58:69:d5:f0  
          inet addr:192.168.1.131  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::215:58ff:fe69:d5f0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6454749 errors:190 dropped:0 overruns:0 frame:190
          TX packets:4407076 errors:0 dropped:301 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:970534668 (925.5 MB)  TX bytes:1725696725 (1.6 GB)
          Interrupt:218 Base address:0x8000 

eth1      Link encap:Ethernet  HWaddr 00:15:58:69:d5:f1  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:219 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16306 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16306 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1367296 (1.3 MB)  TX bytes:1367296 (1.3 MB)

codename46@ARFCOM87:~$ lshw -C Network
WARNING: you should run this program as super-user.
codename46@ARFCOM87:~$ lspci -nn
00:00.0 RAM memory [0500]: nVidia Corporation C51 Host Bridge [10de:02f4] (rev a2)
00:00.1 RAM memory [0500]: nVidia Corporation C51 Memory Controller 0 [10de:02fa] (rev a2)
00:00.2 RAM memory [0500]: nVidia Corporation C51 Memory Controller 1 [10de:02fe] (rev a2)
00:00.3 RAM memory [0500]: nVidia Corporation C51 Memory Controller 5 [10de:02f8] (rev a2)
00:00.4 RAM memory [0500]: nVidia Corporation C51 Memory Controller 4 [10de:02f9] (rev a2)
00:00.5 RAM memory [0500]: nVidia Corporation C51 Host Bridge [10de:02ff] (rev a2)
00:00.6 RAM memory [0500]: nVidia Corporation C51 Memory Controller 3 [10de:027f] (rev a2)
00:00.7 RAM memory [0500]: nVidia Corporation C51 Memory Controller 2 [10de:027e] (rev a2)
00:04.0 PCI bridge [0604]: nVidia Corporation C51 PCI Express Bridge [10de:02fb] (rev a1)
00:08.0 RAM memory [0500]: nVidia Corporation MCP55 Memory Controller [10de:0369] (rev a1)
00:09.0 ISA bridge [0601]: nVidia Corporation MCP55 LPC Bridge [10de:0360] (rev a2)
00:09.1 SMBus [0c05]: nVidia Corporation MCP55 SMBus [10de:0368] (rev a2)
00:09.2 RAM memory [0500]: nVidia Corporation MCP55 Memory Controller [10de:036a] (rev a2)
00:0a.0 USB Controller [0c03]: nVidia Corporation MCP55 USB Controller [10de:036c] (rev a1)
00:0a.1 USB Controller [0c03]: nVidia Corporation MCP55 USB Controller [10de:036d] (rev a2)
00:0c.0 IDE interface [0101]: nVidia Corporation MCP55 IDE [10de:036e] (rev a1)
00:0d.0 IDE interface [0101]: nVidia Corporation MCP55 SATA Controller [10de:037f] (rev a2)
00:0d.1 IDE interface [0101]: nVidia Corporation MCP55 SATA Controller [10de:037f] (rev a2)
00:0d.2 IDE interface [0101]: nVidia Corporation MCP55 SATA Controller [10de:037f] (rev a2)
00:0e.0 PCI bridge [0604]: nVidia Corporation MCP55 PCI bridge [10de:0370] (rev a2)
00:10.0 Bridge [0680]: nVidia Corporation MCP55 Ethernet [10de:0373] (rev a2)
00:11.0 Bridge [0680]: nVidia Corporation MCP55 Ethernet [10de:0373] (rev a2)
00:12.0 PCI bridge [0604]: nVidia Corporation MCP55 PCI Express bridge [10de:0376] (rev a2)
00:16.0 PCI bridge [0604]: nVidia Corporation MCP55 PCI Express bridge [10de:0375] (rev a2)
00:17.0 PCI bridge [0604]: nVidia Corporation MCP55 PCI Express bridge [10de:0377] (rev a2)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
01:00.0 VGA compatible controller [0300]: nVidia Corporation GeForce 8800 GT [10de:0611] (rev a2)
02:08.0 FireWire (IEEE 1394) [0c00]: Texas Instruments TSB82AA2 IEEE-1394b Link Layer Controller [104c:8025] (rev 01)
02:0a.0 Multimedia audio controller [0401]: Creative Labs SB Audigy LS [1102:0007]


---

### Post by pytheas22 on 2008-09-15
Strange, strange stuff.  It looks like memory registers or something are being dumped into dmesg.  I've never seen that before.  The next time the problem occurs, could you please post the output of the command:
```

dmesg
```

all by itself?  It will be really long, but I think the only way to figure this out is to see all of dmesg ('dmesg | tail' just outputs the most recent entries).  Sorry to ask you to post this again, but I can't make anything out of what's above, other than that something weird is going on.

Also, your 'lshw -C Network' output returned nothing.  Did you wait a few seconds (it takes a few seconds to gather the information and display it)?  Otherwise, something quite strange is going on there as well.  It should never return a blank line.

---

### Post by Codename46 on 2008-09-15
> **pytheas22 said:**
> Strange, strange stuff.  It looks like memory registers or something are being dumped into dmesg.  I've never seen that before.  The next time the problem occurs, could you please post the output of the command:
```

dmesg
```

all by itself?  It will be really long, but I think the only way to figure this out is to see all of dmesg ('dmesg | tail' just outputs the most recent entries).  Sorry to ask you to post this again, but I can't make anything out of what's above, other than that something weird is going on.

Also, your 'lshw -C Network' output returned nothing.  Did you wait a few seconds (it takes a few seconds to gather the information and display it)?  Otherwise, something quite strange is going on there as well.  It should never return a blank line.
I will post the results of just typing in "dmesg" when it happens again.

As for the "lshw -C Network" output, it first displays "PCI (sysfs) " for a few seconds, then quickly cycles through some more text (went too fast, couldn't get it) and then returns nothing.

---

### Post by Crafty Kisses on 2008-09-15
Hey Codename! :lolflag:

It could be packet loss, well it certainly sounds like it.

Packet loss can be caused by a number of factors, including signal degradation over the network medium, oversaturated network links, corrupted packets rejected in-transit, faulty networking hardware, maligned system drivers or network applications, or normal routing routines.

Some network transport protocols such as TCP provide for reliable delivery of packets. In the event of packet loss, the receiver asks for retransmission or the sender automatically resends any segments that have not been acknowledged.

---

### Post by Codename46 on 2008-09-15
> **Codename said:**
> Hey Codename! :lolflag:

It could be packet loss, well it certainly sounds like it.

Packet loss can be caused by a number of factors, including signal degradation over the network medium, oversaturated network links, corrupted packets rejected in-transit, faulty networking hardware, maligned system drivers or network applications, or normal routing routines.

Some network transport protocols such as TCP provide for reliable delivery of packets. In the event of packet loss, the receiver asks for retransmission or the sender automatically resends any segments that have not been acknowledged.

Only way to make sure it to leave my computer on in Windows for a long time and see if I have the same problem.

If not then that means the problem is isolated to being a software problem only....right?

---

### Post by Crafty Kisses on 2008-09-15
That's possible or even possibly hardware.

---

### Post by Codename46 on 2008-09-27
> **Codename said:**
> That's possible or even possibly hardware.

Well I left my computer on in Windows for hours and this problem doesn't occur.

It's still occurring in Linux. I think it does it then there's heavy download traffic for a long time (e.g bittorrent)

Still need help here :(

---

### Post by pytheas22 on 2008-09-27
If it's software, then you could probably fix the problem by either upgrading to a more recent build of the driver, or using a different driver.  I think your card uses madwifi, so if you want to install the latest version, you can use the script available [here]("http://ubuntuforums.org/showthread.php?t=798485").

The other option is to use ndiswrapper, which would drive the card using Windows drivers.  [This guide]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper") explains generically how to get ndiswrapper working; if you need more specific help, let us know.

Also, I'm not actually certain that your card uses madwifi--Google just suggests that it does.  If you want to know for sure, please post the output of the command:
```

lshw -C Network
```

---

