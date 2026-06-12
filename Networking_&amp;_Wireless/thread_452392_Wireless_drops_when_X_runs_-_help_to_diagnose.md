---
title: "Wireless drops when X runs - help to diagnose?"
date: 2007-05-23
forum: Networking &amp; Wireless
---

### Post by prof_booty on 2007-05-23
Hi:

I'm using Feisty with a Netgear WG111v2 wireless adapter which uses DHCP from a Linksys WRT54G access point.  Loaded drivers fine with ndiswrapper, everything is happy.  I can ssh to my machine from work all day, but when I come home at night and log in to X, invariably the connection drops out.  I suspect that it has to do with X or some program running, but maybe it's my neighbor's microwave?  Or something I haven't thought of?  Does anyone have any ideas as to how I might go about finding the cause?

Here are some details, addresses redacted to protect the innocent:

[prof@tardis:~]$ ifconfig wlan0
wlan0     Link encap:Ethernet  HWaddr 00:14:6X:X9:8X:1X  
          inet addr:192.168.1.112  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: xx80::214:6xxx:xxx9:8d1x/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3074 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2566 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1212380 (1.1 MiB)  TX bytes:347332 (339.1 KiB)

[prof@tardis:~]$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"redacted"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:18:X8:XC:1X:XX   
          Bit Rate=18 Mb/s   Tx-Power:20 dBm   Sensitivity=0/3  
          RTS thr=2346 B   Fragment thr=2400 B   
          Power Management:off
          Link Quality:43/100  Signal level:-68 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:1  Invalid misc:569174744   Missed beacon:0

---

