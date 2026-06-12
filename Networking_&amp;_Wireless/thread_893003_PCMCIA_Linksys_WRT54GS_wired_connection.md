---
title: "PCMCIA Linksys WRT54GS wired connection"
date: 2008-08-17
forum: Networking &amp; Wireless
---

### Post by gh1138 on 2008-08-17
Ubuntu PC:  older Compaq Presario 1277 laptop
PMCIA Card: 3Com Etherlink III 3C589D-TP
Router:  Linksys Wireless Broadband Routher WRT54GS
Modem:  Westell DSL USB/Ethernet modem (connected by Ethernet)

[FONT="Arial"]Hello,

Just loaded Ubuntu 8.04 Alternate on an older Compaq laptop.  I'm trying to connect to a Linksys router through a wired connection.  I think the laptop recognizes the PCMCIA card, but I can't connect to the router, nor can I connect to the internet when wired directly through the DSL modem.  Also, the front of the routher has indicator lights for the wired connections, and the indicator light for the port the laptop's plugged into is not lit.  FWIW, on the laptop, if I go to Places and then Network, it does show an icon for "Windows Network" but if I double-click on the icon, the new box is empty.

From scanning other posts here, it seems it's good to post the output from 3 terminal commands, so I'm posting below:[/FONT]
[FONT="Times New Roman"][/FONT]
lspci
00:00.0 Host bridge: VIA Technologies, Inc. VT8501 [Apollo MVP4] (rev 03)
00:01.0 PCI bridge: VIA Technologies, Inc. VT8501 [Apollo MVP4 AGP]
00:07.0 ISA bridge: VIA Technologies, Inc. VT82C686 [Apollo Super South] (rev 19)
00:07.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:07.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 0a)
00:07.4 ISA bridge: VIA Technologies, Inc. VT82C686 [Apollo Super ACPI] (rev 20)
00:07.5 Multimedia audio controller: VIA Technologies, Inc. VT82C686 AC97 Audio Controller (rev 21)
00:09.0 Communication controller: Agere Systems 56k WinModem (rev 01)
00:0a.0 CardBus bridge: Texas Instruments PCI1211
01:00.0 VGA compatible controller: Trident Microsystems CyberBlade/i7d (rev 5c)

hammer@ubuntu:~$ lspci -n
00:00.0 0600: 1106:0501 (rev 03)
00:01.0 0604: 1106:8501
00:07.0 0601: 1106:0686 (rev 19)
00:07.1 0101: 1106:0571 (rev 06)
00:07.2 0c03: 1106:3038 (rev 0a)
00:07.4 0601: 1106:3057 (rev 20)
00:07.5 0401: 1106:3058 (rev 21)
00:09.0 0780: 11c1:0441 (rev 01)
00:0a.0 0607: 104c:ac1e
01:00.0 0300: 1023:8420 (rev 5c)
hammer@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:10:4b:ed:15:1d  
          inet6 addr: fe80::210:4bff:feed:151d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:5 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:8590 (8.3 KB)
          Interrupt:3 Base address:0x300 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1978 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1978 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:99092 (96.7 KB)  TX bytes:99092 (96.7 KB)

hammer@ubuntu:~$ 
[FONT="Arial"][/FONT]

Any help is appreciated.  Thanks.

---

