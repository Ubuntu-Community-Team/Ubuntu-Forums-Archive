---
title: "PPPoE can't see my WLAN0 interface"
date: 2005-05-18
forum: Networking &amp; Wireless
---

### Post by padami on 2005-05-18
Hi to all,
I've just installed ndiswrapper for my wlan Broadcomm card, to be connected to an Access Point and ADSL. There is something wrong somewhere and I really hope that you may help me, because I need to connect to Internet!
All things seem configured properly, but the result of pon is the following:

May 18 06:43:34 mario pppd[6969]: Timeout waiting for PADO packets
May 18 06:43:34 mario pppd[6969]: Unable to complete PPPoE Discovery
May 18 06:43:34 mario pppd[6969]: Exit.
May 18 06:48:33 mario pppd[8663]: Plugin rp-pppoe.so loaded.
May 18 06:48:33 mario pppd[8663]: RP-PPPoE plugin version 3.3 compiled against pppd 2.4.2
May 18 06:48:33 mario pppd[8663]: In file /etc/ppp/peers/dsl-provider: unrecognized option 'wlan0'
# Minimalistic default options file for DSL/PPPoE connections

The installation of ndiswrapper was successfully, and a wla0 interface was generated; by the way, pppoeconf found correctly the interface wlan0 and the "network Concentrator". So all things seem OK...
The following is the result of cat /etc/ppp/peers/dsl-provider:

noipdefault
defaultroute
replacedefaultroute
hide-password
#lcp-echo-interval 30
#lcp-echo-failure 4
noauth
persist
#mtu 1492
usepeerdns
plugin rp-pppoe.so wlan0

I thought it was a possible problem of alias, but if I type:
cat /etc/modprobe.d/ndiswrapper
the result is:
alias wlan0 ndiswrapper
(it seems correct)

On the other hand, if I try to ping my Access Point, there is no feedback:
ping 192.168.0.50 
	Destination host unreachable

The weird thing is that if I scan the wireless network and look at iwconfig, the AP is there:

user "mario"
wlan0     IEEE 802.11g  ESSID:"mario6019"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:0F:3D:67:82:03   
          Bit Rate:11 Mb/s   Tx-Power:25 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Encryption key:6D64-3931-6B6F-626D-6439-316F-6B   Security mode:open
          Power Management:off
          Link Quality:100/100  Signal level:-15 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:25735   Missed beacon:0

And ifconfig wlan0 shows a correct IP local address:

wlan0     Link encap:Ethernet  HWaddr 00:90:4B:9F:E8:63  
          inet addr:192.168.0.10  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::290:4bff:fe9f:e863/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:60 (60.0 b)  TX bytes:402 (402.0 b)
          Interrupt:21 Memory:d2004000-d2005fff 

What can I do to solve my problem?

---

