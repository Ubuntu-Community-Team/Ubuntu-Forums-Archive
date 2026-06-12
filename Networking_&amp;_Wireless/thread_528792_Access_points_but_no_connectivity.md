---
title: "Access points but no connectivity"
date: 2007-08-18
forum: Networking &amp; Wireless
---

### Post by Zigbigidorlu on 2007-08-18
My wireless card sees several access points, but whenever I try to connect to any [not just my own], it won't join.  I've only been able to connect once, and that resulted in a signal strength bar image but access to nothing, not even the router firmware (192.168.1.1).

I've looked all over the web for a solution, but everything I've tried has failed.

I'm running Ubuntu 7.04 Feisty and using a Linksys WMP54G v4 wireless card.  I've heard something about firmware for it before, but I don't know how to attain it...

Here's my iwconfig:
lo        no wireless extensions.

eth0      no wireless extensions.

ra0       RT2500 Wireless  ESSID:"NETGEAR"  
          Mode:Managed  Frequency=2.462 GHz  Access Point: 00:90:4C:7E:00:6E   
          Bit Rate:54 Mb/s   Tx-Power:-6 dBm   
          RTS thr:off   Fragment thr:off
          Link Quality=80/100  Signal level=-20 dBm  Noise level:-205 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by Jamie Jackson on 2007-08-19
What's the output of

lshw -C network

---

