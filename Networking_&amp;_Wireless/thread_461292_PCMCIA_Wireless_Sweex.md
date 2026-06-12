---
title: "PCMCIA Wireless Sweex"
date: 2007-06-01
forum: Networking &amp; Wireless
---

### Post by the_tavi on 2007-06-01
Hello all,

Old within computers, very beginner with Linux (Feisty Fawn 7.04 first love ), I am facing a problem that I do not really understand. I have a Laptop IBM ThinkPad T40, improved with an internal original IBM wireless card. Supplementary I use one external PCMCIA Sweex card, that used to be more efficient than the internal (in Windows) when having not very strong wireless network (practically is more efficient pointed in the direction of the wireless router).

Now, my Feisty recognize both of the cards, my network manager is working fine, but the signal of Sweex card is much more weak than in Windows, used in the same conditions. Actually, I cannot connect from the same spot using external card and LINUX instead of Windows. Maybe it is a strange driver, or there is something missing.

Can you please help me with a few ideas? I will post the result of "lspci" below:

Thank you,

Tavi

02:02.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)
Subsystem: Intel Corporation Unknown device 2712
Flags: bus master, medium devsel, latency 64, IRQ 11
Memory at c0200000 (32-bit, non-prefetchable) [size=4K]
Capabilities: <access denied>

02:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (MOB) Ethernet Controller (rev 81)
Subsystem: IBM Thinkpad R50e model 1634
Flags: bus master, medium devsel, latency 66, IRQ 11
Memory at c0201000 (32-bit, non-prefetchable) [size=4K]
I/O ports at 8000 [size=64]
Capabilities: <access denied>

03:00.0 Ethernet controller: Atheros Communications, Inc. AR5005G 802.11abg NIC (rev 01)
Subsystem: Atheros Communications, Inc. TP-Link TL-WN510G Wireless CardBus Adapter
Flags: bus master, medium devsel, latency 168, IRQ 11
Memory at c4000000 (32-bit, non-prefetchable) [size=64K]
Capabilities: <access denied>

---

### Post by tturrisi on 2007-06-01
connect with one, post result of:
iwconfig
connect with other, post result of iwconfig again.

How do you know the signal is weaker?

---

### Post by the_tavi on 2007-06-02
Hi,

How do you know the signal is weaker?

First, by checking the graphical tool from the network manager. I know it is not very reliable, but still, I can see the signal is almost missing for the PCMCIA wireless.
Second, comparing to Windows. I am using one place in the room. When I'm using Windows and trying to connect with PCMCIA wireless (with the appropriate driver of the Sweex PCMCIA board), I can connect having a Fair to Good signal. When I try to connect using Linux and the same PCMCIA board, I am not even getting connected.

Btw, the producer of Sweex Wireless I have didn't bother to provide support for Linux users...


 	connect with one, post result of:
iwconfig
connect with other, post result of iwconfig again.

Case 1: IBM (internal) wireless connected (OK, working well):

eth1      IEEE 802.11g  ESSID:"default"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:13:46:97:29:E2   
          Bit Rate:54 Mb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=55/100  Signal level=-68 dBm  Noise level=-85 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:10

ath0      IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:18 dBm   Sensitivity=0/3  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/94  Signal level=-92 dBm  Noise level=-92 dBm
          Rx invalid nwid:18117  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


Case 2: PCMCIA (external) wireless trying to connect (NOK, actually not connected at all):


eth1      unassociated  ESSID:""  
          Mode:Managed  Channel=0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

ath0      IEEE 802.11g  ESSID:"default"  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:13:46:97:29:E2   
          Bit Rate:1 Mb/s   Tx-Power:18 dBm   Sensitivity=0/3  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=10/94  Signal level=-84 dBm  Noise level=-94 dBm
          Rx invalid nwid:20744  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth1      unassociated  ESSID:""  
          Mode:Managed  Channel=0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

ath0      IEEE 802.11g  ESSID:"default"  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:13:46:97:29:E2   
          Bit Rate:1 Mb/s   Tx-Power:18 dBm   Sensitivity=0/3  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=10/94  Signal level=-85 dBm  Noise level=-95 dBm
          Rx invalid nwid:20757  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

BR,

Tavi

---

