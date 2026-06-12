---
title: "near-worthless wireless"
date: 2007-09-19
forum: Networking &amp; Wireless
---

### Post by dannemil on 2007-09-19
My wireless connection is about to drive me up the wall. It drops in and out and is completely unreliable - BUT THE WIRELESS ROUTER IS IN THE NEXT ROOM ONLY 15 FEET AWAY!

The router is a linksys WRT54GS. I am running Feisty with an internal wireless card (Atheros).

I have tried everything I can think of to fix things but nothing works. Here is some relevant information with addresses etc xx'd out where necessary

dannemil@gvuser-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"x"  Nickname:"x"
          Mode:Managed  Frequency:2.462 GHz  Access Point x.....  
          Bit Rate:54 Mb/s   Tx-Power:18 dBm   Sensitivity=0/3  
          Retry: off   RTS thr: off   Fragment thr: off
          Power Management: off
          Link Quality=40/94  Signal level=-49 dBm  Noise level=-89 dBm
          Rx invalid nwid:376  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Comments: What is that wifi0 interface? As shown below, there is nothing on that interface in my /etc/network/interfaces file.

Also, should I be concerned about the Rx invalid nwid:376 ? Is that a large number for invalid nwid?

..next command 

dannemil@gvuser-desktop:~$ cat /proc/net/wireless
Inter-| sta-|   Quality        |   Discarded packets               | Missed | WE
 face | tus | link level noise |  nwid  crypt   frag  retry   misc | beacon | 21
  ath0: 0004   43.  205.  162.     376      0      0      0      0        0


...next command

dannemil@gvuser-desktop:~$ ifconfig
ath0      Link encap:Ethernet  HWaddr x...
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:28870 errors:0 dropped:0 overruns:0 frame:0
          TX packets:27637 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:25222803 (24.0 MiB)  TX bytes:5194780 (4.9 MiB)

eth0      Link encap:Ethernet  HWaddr x...
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:288 errors:0 dropped:0 overruns:0 frame:0
          TX packets:288 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:25031 (24.4 KiB)  TX bytes:25031 (24.4 KiB)

wifi0     Link encap:UNSPEC  HWaddr 00-13-46-97-52-7E-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:102498 errors:0 dropped:0 overruns:0 frame:103975
          TX packets:88590 errors:63 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:33758963 (32.1 MiB)  TX bytes:9165574 (8.7 MiB)
          Interrupt:20 

Comments: OK, there it is again, the wifi0 interface. Could this be causing problems?

...next command

dannemil@gvuser-desktop:~$ sudo ifup ath0
There is already a pid file /var/run/dhclient.ath0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath0/00:13:46:97:52:7e
Sending on   LPF/ath0/00:13:46:97:52:7e
Sending on   Socket/fallback
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 4
DHCPOFFER from 192.168.1.1
DHCPREQUEST on ath0 to 255.255.255.255 port 67
DHCPACK from 192.168.1.1
bound to 192.168.1.100 -- renewal in 197094 seconds.

Comments: It connects OK, but the reliability is horrible - web pages don't load until refreshed, pings to exterenal ip's sometimes work and 10 secs later they don't.

Here is my /etc/network/interfaces file

auto lo
iface lo inet loopback


auto ath0
iface ath0 inet dhcp
wireless-essid x...
wireless-key x...

-----
Finally, here is some info from /var/log/syslog
Sep 18 23:33:35 gvuser-desktop isakmpd[5874]: pf_key_v2_notify: unexpected message type (13)
Sep 18 23:33:39 gvuser-desktop last message repeated 3 times
Sep 18 23:34:15 gvuser-desktop isakmpd[5874]: pf_key_v2_notify: unexpected message type (15)
Sep 18 23:34:25 gvuser-desktop isakmpd[5874]: pf_key_v2_notify: unexpected message type (13)
Sep 18 23:34:35 gvuser-desktop last message repeated 2 times
Sep 18 23:35:16 gvuser-desktop isakmpd[5874]: pf_key_v2_notify: unexpected message type (15)
Sep 18 23:35:31 gvuser-desktop isakmpd[5874]: transport_send_messages: giving up on message 0x828e6b0, exchange ISAKMP-peer-west
Sep 18 23:35:31 gvuser-desktop isakmpd[5874]: transport_send_messages: either this message did not reach the other peer
Sep 18 23:35:31 gvuser-desktop isakmpd[5874]: transport_send_messages: or the responsemessage did not reach us back
Sep 18 23:35:32 gvuser-desktop isakmpd[5874]: pf_key_v2_notify: unexpected message type (13)
Sep 18 23:36:18 gvuser-desktop isakmpd[5874]: pf_key_v2_notify: unexpected message type (15)
Sep 18 23:36:32 gvuser-desktop isakmpd[5874]: pf_key_v2_notify: unexpected message type (13)
Sep 18 23:37:19 gvuser-desktop isakmpd[5874]: pf_key_v2_notify: unexpected message type (15)
Sep 18 23:37:31 gvuser-desktop isakmpd[5874]: transport_send_messages: giving up on message 0x829c3f0, exchange ISAKMP-peer-west
Sep 18 23:37:31 gvuser-desktop isakmpd[5874]: transport_send_messages: either this message did not reach the other peer
Sep 18 23:37:31 gvuser-desktop isakmpd[5874]: transport_send_messages: or the responsemessage did not reach us back
Sep 18 23:37:33 gvuser-desktop isakmpd[5874]: pf_key_v2_notify: unexpected message type (13)
Sep 18 23:38:24 gvuser-desktop isakmpd[5874]: pf_key_v2_notify: unexpected message type (15)
Sep 18 23:38:29 gvuser-desktop last message repeated 3 times
Sep 18 23:38:34 gvuser-desktop isakmpd[5874]: pf_key_v2_notify: unexpected message type (13)
Sep 18 23:39:10 gvuser-desktop isakmpd[5874]: pf_key_v2_notify: unexpected message type (15)

Are all of these unexpected messages and unreachable peers normal?


I know that is probably tmi, but I have exhausted my meager knowledge of wireless networking to make things work but with no success. As it is, my networking is almost unusable - using a browser becomes torture when every page has to be refreshed before anything will display properly. I am considering going back to carrier pigeons - they're probably more reliable at this point in terms of delivering internet packets :)

[EDIT added additional information]:

dannemil@gvuser-desktop:~$ sudo lshw -C network
Password:
  *-network               
       description: Wireless interface
       product: AR5212 802.11abg NIC
       vendor: Atheros Communications, Inc.
       physical id: 7
       bus info: pci@01:07.0
       logical name: wifi0
       version: 01
       serial: xx,,,
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci driverversion=0.9.4.5 (0.9.3.1) ip=192.168.1.100 latency=168 maxlatency=28 mingnt=10 multicast=yes wireless=IEEE 802.11g
       resources: iomemory:fdef0000-fdefffff irq:20


Jim

---

### Post by him610 on 2007-09-19
The IP address 192.168.1.100 indicates you are connected to your router. From what I have read in various posts in this forum, the Atheros wireless card is one of the easier ones to set up and configure.  
It very well could be your router. I once had a Linksys WRT54G router that for some reason would not maintain its connection with the upstream cable-company-provided cable modem via a 12-inch Cat 5 cable. The cable company wasn't much help either. I wound up installing a wired router (they don't cost much - about $20 bucks) between the cable modem and the Linksys WRT54G and never had another network problem. You might want to check the lease time in the setup of your router; be sure you do this using a wired connection.
Cheers!

---

### Post by Phelan on 2007-09-19
I've had the same problems with the same router (in windows, havn't gotten my wireless working in 'nix *yet*, and the solution of the hard-wired router fixed my problem.

---

### Post by Zaneyard on 2007-09-19
i have a setup with a Linksys WRT54GS
i don't have many problems except for the occasional power cycle to clear the cache.
at the time of these "lags" does a wired computer also do it?
if so its a problem with your connection, modem or service
if not then you have problems with either interference, it happens or the antenna on either your card or "router"
if it is the second option its time for some returns or RMA's, i don't think a dropping connection of that sort is software based
maybe try firmware updates, that made a lightbulb turn on, maybe it is not so not software based

---

