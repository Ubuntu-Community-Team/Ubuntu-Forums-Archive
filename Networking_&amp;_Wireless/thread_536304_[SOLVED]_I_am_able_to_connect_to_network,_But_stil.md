---
title: "[SOLVED] I am able to connect to network, But still have no internet"
date: 2007-08-27
forum: Networking &amp; Wireless
---

### Post by spoonman184 on 2007-08-27
I am able to connect to my network, but I cannot browse the network or install software using appget (or whatever command it is). 

I am using a Tel-something chipset, but unsure which it is. 
Please ask me what commands you would like me to run in the terminal and post.

I have NO internet connection so if I need to install ndiswrapper or another application, please give me instructions on how to install them via USB or other means.

I have no idea how to use ndiswrapper or a compiler, so full instructions would be nice.

---

### Post by Barkingdoggy on 2007-08-27
More info please.  What flavor of Ubuntu are you running?  Is it patched and updated?  Are you networking to your LAN with an Ethernet cable or are you using 802.11a,b, or g?  What do you get when you enter ifconfig and/or iwconfig from the Terminal window?...

---

### Post by spoonman184 on 2007-08-27
Fiesty (7.04) Clean install, no updates (can't connect to internet)
Networking via a wireless card 802.11 g/b
and heres the terminal commands (added a few more):

```
lshw -C network
 *-network:1
       description: Wireless interface
       product: ACX 111 54Mbps Wireless Interface
       vendor: Texas Instruments
       physical id: 9
       bus info: pci@00:09.0
       logical name: wlan0
       version: 00
       serial: 00:40:f4:c7:cc:8c
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=acx_pci latency=64 multicast=yes wireless=IEEE 802.11b+/g+
       resources: iomemory:cfff8000-cfff9fff iomemory:cffa0000-cffbffff irq:5


iwlist scan
lo        Interface doesn't support scanning.
eth0      Interface doesn't support scanning.
wlan0     Scan completed :
          Cell 01 - Address: 00:15:05:25:A2:99
                    ESSID:"ACTIONTEC"
                    Mode:Master
                    Frequency:2.452 GHz (Channel 9)
                    Quality=33/100  Signal level=6/100  Noise level=0/100
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 22 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
          Cell 02 - Address: 00:0D:3A:25:72:03
                    ESSID:"Chaotic_MN"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=42/100  Signal level=19/100  Noise level=0/100
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 03 - Address: 00:12:17:26:06:D2
                    ESSID:"linksys"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=35/100  Signal level=9/100  Noise level=0/100
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 04 - Address: 00:20:E0:1F:F0:29
                    ESSID:"SPORT"
                    Mode:Master
                    Frequency:2.452 GHz (Channel 9)
                    Quality=34/100  Signal level=8/100  Noise level=0/100
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 22 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
          Cell 05 - Address: 00:11:45:02:3B:2B
                    ESSID:"SAP0063"
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality=31/100  Signal level=4/100  Noise level=0/100
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
          Cell 06 - Address: 00:11:45:02:43:C5
                    ESSID:"SAP0071"
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality=34/100  Signal level=8/100  Noise level=0/100
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
          Cell 07 - Address: 00:12:17:0A:0B:F8
                    ESSID:"linksys"
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality=32/100  Signal level=5/100  Noise level=0/100
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
          Cell 08 - Address: 46:00:C9:00:5B:01
                    ESSID:"SST-PR-1"
                    Mode:Ad-Hoc
                    Frequency:2.437 GHz (Channel 6)
                    Quality=33/100  Signal level=6/100  Noise level=0/100
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
          Cell 09 - Address: 46:00:C9:00:5B:01
                    ESSID:"SST-PR-1"
                    Mode:Ad-Hoc
                    Frequency:2.437 GHz (Channel 6)
                    Quality=34/100  Signal level=7/100  Noise level=0/100
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s


iwconfig
lo        no wireless extensions.
eth0      no wireless extensions.
wlan0     IEEE 802.11b+/g+  ESSID:""  Nickname:"acx v0.3.36"
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power=15 dBm   Sensitivity=1/3  
          Retry min limit:7   RTS thr:off   
          Power Management:off
          Link Quality=43/100  Signal level=20/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


ifconfig
eth0      Link encap:Ethernet  HWaddr 00:07:95:34:B9:13  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:12 Base address:0xcc00 
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6160 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6160 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:482064 (470.7 KiB)  TX bytes:482064 (470.7 KiB)
wlan0     Link encap:Ethernet  HWaddr 00:40:F4:C7:CC:8C  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:10 errors:0 dropped:0 overruns:0 frame:0
          TX packets:96 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:736 (736.0 b)  TX bytes:12216 (11.9 KiB)
          Interrupt:5 Base address:0x8000 

lspci
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 730 Host (rev 02)
00:00.1 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev d0)
00:01.0 ISA bridge: Silicon Integrated Systems [SiS] SiS85C503/5513 (LPC Bridge)
00:01.1 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 82)
00:01.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 07)
00:01.3 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 07)
00:01.4 Multimedia audio controller: Silicon Integrated Systems [SiS] SiS PCI Audio Accelerator (rev 02)
00:01.6 Modem: Silicon Integrated Systems [SiS] AC'97 Modem Controller (rev a0)
00:02.0 PCI bridge: Silicon Integrated Systems [SiS] Virtual PCI-to-PCI bridge (AGP)
00:09.0 Network controller: Texas Instruments ACX 111 54Mbps Wireless Interface
01:00.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200 PRO] (rev 01)
01:00.1 Display controller: ATI Technologies Inc RV280 [Radeon 9200 PRO] (Secondary) (rev 01)
```

---

### Post by spoonman184 on 2007-08-27
I am trying to connect to 'Chaotic_MN'

---

### Post by KCPokes on 2007-08-27
I believe it is a case of acting like it is connecting, but if you look at your ifconfig statement, you have no ip address assigned.  For example, here is my ifconfig:

> 
webadmin@Gubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:E0:B8:D7:E4:7C  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

eth0:avah Link encap:Ethernet  HWaddr 00:E0:B8:D7:E4:7C  
          inet addr:169.254.10.210  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:24 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1927 (1.8 KiB)  TX bytes:1927 (1.8 KiB)

wlan0     Link encap:Ethernet  HWaddr 00:C0:A8:EC:00:8C  
          inet addr:192.168.1.199  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2c0:a8ff:feec:8c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:172267 errors:0 dropped:0 overruns:0 frame:0
          TX packets:122801 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:174865378 (166.7 MiB)  TX bytes:27402587 (26.1 MiB)

wmaster0  Link encap:UNSPEC  HWaddr 00-C0-A8-EC-00-8C-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)


I'd step back and look at your wireless config and keys.

---

### Post by spoonman184 on 2007-08-28
And what else should I do besides look at them? I'm rather new to this whole thing.

---

### Post by spoonman184 on 2007-08-28
I figured out how to get it to work. In network configuration, I selected the wireless option, then properties. I selected static IP and entered all the old information that I had when I was running Windows XP. Then, I selected DHCP which is what my network uses. Thinking this wouldn't solve anything, I tried pinging my router to see if it would detect it. Viola! I got packets back! This was the first time I managed to get them back, so I fired up Firefox (no pun intended) and I got it to work.

Kudos for nubos!

---

