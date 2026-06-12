---
title: "I can't connect with Ethernet 3Com Corporation 3c556 Hurricane CardBus Cyclone"
date: 2008-12-07
forum: New to Ubuntu
---

### Post by the8thstar on 2008-12-07
Hello,

I have a a 3Com Corporation 3c556 Hurricane CardBus Cyclone ethernet card in an old Dell that I'm trying to connect to the internet through Windows XP but it can't find any connection.

For the record I already do this through my other computer (see sig below) so I don't think Windows is at fault here. I have #! Crunchbang Linux installed (Ubuntu 8.10 + OpenBox).

Thanks for your help!

> the8thstar@the8thstar-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
00:03.0 CardBus bridge: Texas Instruments PCI1420 PC card Cardbus Controller
00:03.1 CardBus bridge: Texas Instruments PCI1420 PC card Cardbus Controller
00:07.0 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 03)
00:08.0 Multimedia audio controller: ESS Technology ES1983S Maestro-3i PCI Audio Accelerator (rev 10)
00:10.0 Ethernet controller: 3Com Corporation 3c556 Hurricane CardBus [Cyclone] (rev 10)
00:10.1 Communication controller: 3Com Corporation Mini PCI 56k Winmodem (rev 10)
01:00.0 VGA compatible controller: ATI Technologies Inc Rage Mobility M3 AGP 2x (rev 02)

the8thstar@the8thstar-laptop:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:04:76:40:76:f5  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:11 Base address:0xec00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1172 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1172 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:58792 (58.7 KB)  TX bytes:58792 (58.7 KB)

pan0      Link encap:Ethernet  HWaddr 12:23:fe:e7:4b:18  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)



---

### Post by the8thstar on 2008-12-10
bump

---

### Post by louieb on 2008-12-10
The only thing I can think of is the DHCP service is not starting.  If I remember right click on my computer > manage > services. Then check to see if DHCP is running.  

BTW: the forum does have a Widows section.

---

### Post by the8thstar on 2008-12-12
Thanks, but there is no such option in #! CrunchBang Linux. And the problem is not related to Windows but to Linux here.

---

