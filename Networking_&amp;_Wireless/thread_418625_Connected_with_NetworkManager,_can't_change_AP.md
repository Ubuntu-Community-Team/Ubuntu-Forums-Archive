---
title: "Connected with NetworkManager, can't change AP"
date: 2007-04-22
forum: Networking &amp; Wireless
---

### Post by Thav on 2007-04-22
Hi, just upgraded from Dapper to Feisty, had to go through and remove everything except for lo in /etc/network/interfaces to get nm-applet to run properly. Anyway, I'm connected now to a friend's router, but when I click on the nm-applet system tray icon and choose another wireless network, it doesn't even try to connect, just stays connected to the current one. I'd like to be able to choose another network since the signal strength is better and my friend's router will be going away in a couple weeks.

Running this on a Thinkpad T40. I've tried reading through a number of other threads, but I've only found people unable to connect, not unable to change connections. Any advice?  Thanks in advance.

lspci - ethernet bits
```
02:01.0 Ethernet controller: Intel Corporation 82540EP Gigabit Ethernet Controller (Mobile) (rev 03)
02:02.0 Ethernet controller: Atheros Communications, Inc. AR5211 802.11ab NIC (rev 01)
```

iwconfig
```
lo        no wireless extensions.

eth0      no wireless extensions.

irda0     no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11b  ESSID:"Laser Express"  Nickname:""
          Mode:Managed  Frequency:2.427 GHz  Access Point: 00:11:24:03:1A:D3   
          Bit Rate:2 Mb/s   Tx-Power:0 dBm   Sensitivity=0/3  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=35/94  Signal level=-63 dBm  Noise level=-98 dBm
          Rx invalid nwid:7750  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

ifconfig
```
ath0      Link encap:Ethernet  HWaddr 00:05:4E:40:ED:3E  
          inet addr:192.168.0.105  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::205:4eff:fe40:ed3e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7240 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4684 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:6274467 (5.9 MiB)  TX bytes:627946 (613.2 KiB)

eth0      Link encap:Ethernet  HWaddr 00:0D:60:10:98:BB  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Base address:0x8000 Memory:c0220000-c0240000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:7 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:388 (388.0 b)  TX bytes:388 (388.0 b)

wifi0     Link encap:UNSPEC  HWaddr 00-05-4E-40-ED-3E-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:42660 errors:0 dropped:0 overruns:0 frame:440
          TX packets:5211 errors:30 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:10637253 (10.1 MiB)  TX bytes:787538 (769.0 KiB)
          Interrupt:11 

```

---

### Post by amohanty on 2007-04-22
> Running this on a Thinkpad T40. I've tried reading through a number of other threads, but I've only found people unable to connect, not unable to change connections. Any advice? Thanks in advance.


I dont use the applet toi switch, so I cannot really help you there. However from the command line you cando the following:

iwlist ath0 sc

To scan for and get all APs in the area. Then if you have the one you want try:

sudo iwconfig ath0 essid <ap_ssid> mode managed key <ap_key>

HTH
AM

---

