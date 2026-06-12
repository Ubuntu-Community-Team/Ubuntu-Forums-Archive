---
title: "Terrible Atheros signal strength?"
date: 2007-07-21
forum: Networking &amp; Wireless
---

### Post by ViperKnight on 2007-07-21
I seem to be having serious issues with my Atheros card in my desktop (Running Feisty 64bit).

It has a D-Link Airplus DWL-G520 card in it and I only get about 20-25% signal strength in my bedroom which is only about 15m away from my router!  I've read reports of the signal strength reading being innaccurate, but I'm also getting terrible performance with VNC and I can't use my AmaroK HTML control because it's simply too slow.  Even VNC at 8-bit colour is slow.

However, the odd thing is, Windows XP works fine and shows "Very Good" signal strength (1 bar short of full strength) and VNC flies at 24-bit colour.  So it can't be the card itself.  To make things worse, I'm sending this from my laptop which is right next to my desktop, and it reads usually 70-80% signal strength, but it has an Intel PRO2200 chip:confused:

btw: I have a ZyXEL P-334WT Router which apparently aren't too bad.
Here's the iwconfig from my desktop:
```
viperknight@vk-desktop:~$ iwconfig ath0
ath0      IEEE 802.11g  ESSID:"ZyXEL"  Nickname:""
          Mode:Managed  Frequency:2.457 GHz  Access Point: 00:13:49:53:36:72   
          Bit Rate:36 Mb/s   Tx-Power:16 dBm   Sensitivity=0/3  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=23/94  Signal level=-72 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```
Here's the iwconfig from my Laptop just incase:
```

eth1      IEEE 802.11g  ESSID:"ZyXEL"  
          Mode:Managed  Frequency:2.457 GHz  Access Point: 00:13:49:53:36:72   
          Bit Rate:11 Mb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=67/100  Signal level=-60 dBm  Noise level=-89 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:800  Invalid misc:0   Missed beacon:3

```

If I can't fix this looks like I'll have to break out my huge cable too hook up the desktop with:(

---

### Post by moore.bryan on 2007-07-21
*i'm sorry if this is a silly question, but are you using the latest madwifi drivers for the ath card?*

---

### Post by damir_1105 on 2007-07-21
Antenna Diversity 

Antenna diversity is the term used when the receiver and transmitter use multiple antennas in order to improve the quality of reception/transmission. Many Atheros radios have two antenna connectors which allows you to connect two antennas.

You will definitely want to disable transmitter diversity if you only have one antenna connected. Otherwise 50% of your broadcast and unicast packets (ARP, OSPF) will go out the wrong antenna. 

Antenna diversity can be controlled using sysctl (/proc/sys/dev/wifiX/{diversity,txantenna,rxantenna}):

```
diversity:
    0: no
    1: yes

txantenna and rxantenna:
    0: auto
    1: antenna 1
    2: antenna 2
```

For example, to disable diversity and select antenna 1 for receive and transmit you'd do the following:

```
    sysctl -w dev.wifi0.diversity=0
    sysctl -w dev.wifi0.txantenna=1
    sysctl -w dev.wifi0.rxantenna=1 
```

---

