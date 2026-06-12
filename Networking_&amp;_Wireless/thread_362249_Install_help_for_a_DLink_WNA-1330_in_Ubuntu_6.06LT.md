---
title: "Install help for a DLink WNA-1330 in Ubuntu 6.06LTS"
date: 2007-02-15
forum: Networking &amp; Wireless
---

### Post by Bubbasheeko on 2007-02-15
I had purchased a WNA-1330 for my laptop when I was running...Windows(..ech).  I have installed  Ubuntu 6.06 LTS.  I am unable to use my wireless adapter. 

I had tried to use ndiswrapper to install the INF from the DLink driver CD, shows it installed and that the hardware was present, however, the LED's are flashing alternately so I know that it was not working.  I have set the network name and the key.

Here is some info. lspci -v shows the following about the DLink wireless network adapter.  

0000:06:00.0 Ethernet controller: Atheros Communications, Inc.: Unknown device 001a (rev 01)
        Subsystem: D-Link System Inc: Unknown device 3a1c
        Flags: bus master, medium devsel, latency 168, IRQ 11
        Memory at 26000000 (32-bit, non-prefetchable) [size=64K]
        Capabilities: [44] Power Management version 2

So I know it is using Atheros as the chipset, but have not been able to find something to help me with the installation of the support for the Atheros chipset.  Knowing that I have Atheros installed by looking into the restricted installations in Synaptic.

ifconfig shows:

root@kdavidson-laptop:/home/kdavidson# ifconfig
ath0      Link encap:Ethernet  HWaddr 00:15:E9:D9:21:1B
          inet6 addr: fe80::215:e9ff:fed9:211b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:151 errors:103 dropped:0 overruns:0 frame:103
          TX packets:0 errors:1 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:200
          RX bytes:9502 (9.2 KiB)  TX bytes:0 (0.0 b)
          Interrupt:11 Memory:d0ca0000-d0cb0000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:9 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:472 (472.0 b)  TX bytes:472 (472.0 b)

iwconfig shows:

root@kdavidson-laptop:/home/kdavidson# iwconfig
lo        no wireless extensions.

sit0      no wireless extensions.

ath0      IEEE 802.11g  ESSID:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:40:96:54:B7:E5
          Bit Rate:1 Mb/s   Tx-Power:18 dBm   Sensitivity=0/3
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=0/94  Signal level=-95 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:1  Invalid misc:1   Missed beacon:0

I noticed in this one that the ESSID is not set, and yet it is in the network properties, but this does show that there is no link between the DLink router and this network adapter.

---

### Post by Bubbasheeko on 2007-02-15
Okay, I decided to look at Wifi Radar.  Here is the strange thing, it is connecting to the router in some sort of way.  The IP address picked up was for that network adapter - in Windows as I am partitioned with both Windows and Ubuntu.  192.168.10.11.   Wifi Radar picked up the network and allowed me to set up a profile.  I did this and the IP address was received.  However, I am still seeing the issues with the intermittent LED's.  So something is causing the adapter to drop it's connection.  Any thoughts?

---

### Post by Bubbasheeko on 2007-02-15
Solved.

I discovered the LED's were not working correctly on the adapter and not to go by them.  I turned the security down on my router so that was none, and went from there.

I ended up using WPA_Suplicant and had no issues after that.

---

