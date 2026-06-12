---
title: "Network doesnt work with ASUS M2A-VM in Linux"
date: 2007-09-20
forum: Networking &amp; Wireless
---

### Post by Frenezo on 2007-09-20
Once I had a working Ubuntu on my machine (ASUS M2A-VM, 690G ATI CS). Then I reformatted it and installed Windows XP on it. After a while I installed Ubuntu again and... NETWORK is BROKEN! I tried 7.04 & 7.10 both 32 and 64bit and another Live-Distribution (Knoppix).

I checked the cable, its okay. I also tried to link 2 computers directly with no success. WindowsXP works fine, but in all Linux distributions the NetworkLamp on the Mainboard isnt even on. The only thing I changed is a BIOS-upgrade from 0301 to 1101, but it's difficult to downgrade it. I also tried to enable/disable HPET in BIOS.

Network isnt supposed to be gone after a BIOS upgrade, thats strange. But I have no idea what else I could have done wrong. Does anyone got an idea? Cause otherwise I think this is a Linux or ASUS bug I'd like to file.

---

### Post by Frenezo on 2007-09-20
ifconfig when I use DHCP:

eth0      Protokoll:Ethernet  Hardware Adresse 00:1A:92:75:2B:7B  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          Kollisionen:0 Sendewarteschlangenlänge:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b) 
          Interrupt:19 Basisadresse:0x8000 

eth0:avah Protokoll:Ethernet  Hardware Adresse 00:1A:92:75:2B:7B  
          inet Adresse:169.254.5.177  Bcast:169.254.255.255  Maske:255.255.0.0 
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          Interrupt:19 Basisadresse:0x8000 

lo        Protokoll:Lokale Schleife  
          inet Adresse:127.0.0.1  Maske:255.0.0.0 
          inet6 Adresse: ::1/128 Gültigkeitsbereich:Maschine 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:10 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:10 errors:0 dropped:0 overruns:0 carrier:0 
          Kollisionen:0 Sendewarteschlangenlänge:0 
          RX bytes:844 (844.0 b)  TX bytes:844 (844.0 b) 

---------------------------------------------------------------------------------------------------------------------
ifconfig when I use manual IP:

eth0      Protokoll:Ethernet  Hardware Adresse 00:1A:92:75:2B:7B  
          inet Adresse:192.168.0.15  Bcast:192.168.0.255  Maske:255.255.255.0 
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          Kollisionen:0 Sendewarteschlangenlänge:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b) 
          Interrupt:19 Basisadresse:0x8000 

lo        Protokoll:Lokale Schleife  
          inet Adresse:127.0.0.1  Maske:255.0.0.0 
          inet6 Adresse: ::1/128 Gültigkeitsbereich:Maschine 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:35 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:35 errors:0 dropped:0 overruns:0 carrier:0 
          Kollisionen:0 Sendewarteschlangenlänge:0 
          RX bytes:2774 (2.7 KiB)  TX bytes:2774 (2.7 KiB)

---

### Post by Frenezo on 2007-09-21
Recompiling the driver didnt work neither.

---

