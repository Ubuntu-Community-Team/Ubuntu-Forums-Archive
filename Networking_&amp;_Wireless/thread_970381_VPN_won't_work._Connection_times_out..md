---
title: "VPN won't work. Connection times out."
date: 2008-11-04
forum: Networking &amp; Wireless
---

### Post by gomesp on 2008-11-04
Hi all,

I recently upgraded to version 8.10 (desktop) and since then my VPN connections stopped working. 

After a few initial problems I could "almost" put the vpn to work. The issue that I have is that it tries to connect but eventually times-out.

That is what I see in my syslog:

Nov  4 11:38:22  NetworkManager: <info>  VPN connection 'VPN1' (Connect) reply received. 
Nov  4 11:38:22  pppd[10536]: Plugin /usr/lib/pppd/2.4.4/nm-pptp-pppd-plugin.so loaded.
Nov  4 11:38:22  pppd[10536]: pppd 2.4.4 started by root, uid 0
Nov  4 11:38:22  pptp[10538]: nm-pptp-service-10532 log[main:pptp.c:314]: The synchronous pptp option is NOT activated 
Nov  4 11:38:22  pppd[10536]: Using interface ppp0
Nov  4 11:38:22  pppd[10536]: Connect: ppp0 <--> /dev/pts/2
Nov  4 11:38:53  pppd[10536]: LCP: timeout sending Config-Requests 
Nov  4 11:38:53  NetworkManager: <info>  VPN plugin failed: 1 
Nov  4 11:38:53  pppd[10536]: Connection terminated.
Nov  4 11:38:53  NetworkManager: <info>  VPN plugin failed: 1 
Nov  4 11:38:53  pppd[10536]: Modem hangup
Nov  4 11:38:58  pppd[10536]: Exit.
Nov  4 11:38:58  NetworkManager: <info>  VPN plugin failed: 1 
Nov  4 11:38:58  NetworkManager: <info>  VPN plugin state changed: 6 
Nov  4 11:38:58  NetworkManager: <info>  VPN plugin state change reason: 0 
Nov  4 11:38:58  NetworkManager: <WARN>  connection_state_changed(): Could not process the request because no VPN connection was active. 
Nov  4 11:38:58  NetworkManager: <info>  (eth0): writing resolv.conf to /sbin/resolvconf 
Nov  4 11:38:58  NetworkManager: <info>  Policy set 'Auto eth0' (eth0) as default for routing and DNS. 
Nov  4 11:39:10  NetworkManager: <debug> [1225795150.951386] ensure_killed(): waiting for vpn service pid 10532 to exit 
Nov  4 11:39:10  NetworkManager: <debug> [1225795150.951727] ensure_killed(): vpn service pid 10532 cleaned up

---

### Post by superprash2003 on 2008-11-04
are you able to ping the vpn server successfully?? post output of /etc/resolv.conf after you are connected to vpn server..

---

### Post by guepe on 2008-11-26
I have _exactly_ the same problem !!!
It seems to be a copy paste of the log from pptp.

Here is my /etc/resolv.conf

nameserver 132.207.144.2
search polymtl.ca


It seems perfectly good to me (yes it is from ecole polytechnique in montreal)

---

### Post by guepe on 2008-11-27
I have complementary informations : a tcpdump while trying to authenticate to VPN server.

```
xglurb@xglurb-laptop:~$ sudo tcpdump -i wlan0
tcpdump: verbose output suppressed, use -v or -vv for full protocol decode
listening on wlan0, link-type EN10MB (Ethernet), capture size 96 bytes
16:30:25.208084 IP xglurb-laptop.local.52549 > charles.cdec.polymtl.ca.domain: 55467+ A? srv-vpn01.polymtl.ca. (38)
16:30:25.209195 IP xglurb-laptop.local.46941 > charles.cdec.polymtl.ca.domain: 53333+ PTR? 2.144.207.132.in-addr.arpa. (44)
16:30:25.210513 IP charles.cdec.polymtl.ca.domain > xglurb-laptop.local.52549: 55467* 1/3/3 A srv-vpn01.polymtl.ca (177)
16:30:25.211515 IP charles.cdec.polymtl.ca.domain > xglurb-laptop.local.46941: 53333* 1/3/3 (191)
16:30:25.211800 IP xglurb-laptop.local.60788 > charles.cdec.polymtl.ca.domain: 49418+ PTR? 103.219.207.132.in-addr.arpa. (46)
16:30:25.213823 IP charles.cdec.polymtl.ca.domain > xglurb-laptop.local.60788: 49418 NXDomain* 0/1/0 (110)
16:30:25.215255 IP xglurb-laptop.local.43190 > charles.cdec.polymtl.ca.domain: 48194+ PTR? 10.228.207.132.in-addr.arpa. (45)
16:30:25.217587 IP charles.cdec.polymtl.ca.domain > xglurb-laptop.local.43190: 48194* 2/2/2[|domain]
16:30:25.268449 IP xglurb-laptop.local.34032 > srv-vpn01.polymtl.ca.1723: S 759863883:759863883(0) win 5744 <mss 1436,sackOK,timestamp 3234017 0,nop,wscale 6>
16:30:28.265786 IP xglurb-laptop.local.34032 > srv-vpn01.polymtl.ca.1723: S 759863883:759863883(0) win 5744 <mss 1436,sackOK,timestamp 3234767 0,nop,wscale 6>
16:30:34.265790 IP xglurb-laptop.local.34032 > srv-vpn01.polymtl.ca.1723: S 759863883:759863883(0) win 5744 <mss 1436,sackOK,timestamp 3236267 0,nop,wscale 6>
16:30:46.265787 IP xglurb-laptop.local.34032 > srv-vpn01.polymtl.ca.1723: S 759863883:759863883(0) win 5744 <mss 1436,sackOK,timestamp 3239267 0,nop,wscale 6>
16:30:51.265780 arp who-has 132.207.218.1 tell xglurb-laptop.local
16:30:51.266095 IP xglurb-laptop.local.55697 > charles.cdec.polymtl.ca.domain: 339+ PTR? 1.218.207.132.in-addr.arpa. (44)
16:30:51.268319 arp reply 132.207.218.1 is-at 00:d0:03:56:74:00 (oui Unknown)
16:30:51.271412 IP charles.cdec.polymtl.ca.domain > xglurb-laptop.local.55697: 339 NXDomain* 0/1/0 (108)
16:30:51.373880 IP xglurb-laptop.local.mdns > 224.0.0.251.mdns: 0 PTR (QM)? 1.218.207.132.in-addr.arpa. (44)
16:30:52.381880 IP xglurb-laptop.local.mdns > 224.0.0.251.mdns: 0 PTR (QM)? 1.218.207.132.in-addr.arpa. (44)
16:30:54.389904 IP xglurb-laptop.local.mdns > 224.0.0.251.mdns: 0 PTR (QM)? 1.218.207.132.in-addr.arpa. (44)
16:30:56.278368 IP xglurb-laptop.local.57731 > charles.cdec.polymtl.ca.domain: 42161+ PTR? 251.0.0.224.in-addr.arpa. (42)
16:30:56.280572 IP charles.cdec.polymtl.ca.domain > xglurb-laptop.local.57731: 42161 NXDomain 0/1/0 (100)
16:30:56.385933 IP xglurb-laptop.local.mdns > 224.0.0.251.mdns: 0 PTR (QM)? 251.0.0.224.in-addr.arpa. (42)
16:30:57.389896 IP xglurb-laptop.local.mdns > 224.0.0.251.mdns: 0 PTR (QM)? 251.0.0.224.in-addr.arpa. (42)
16:30:59.393878 IP xglurb-laptop.local.mdns > 224.0.0.251.mdns: 0 PTR (QM)? 251.0.0.224.in-addr.arpa. (42)

```

Any help/ideas ?

---

### Post by guepe on 2008-11-28
No one ? :confused:

---

### Post by apanloco on 2009-04-07
Did you solve this? I have the same problem now. Log looks identical, trying to connect VPN (PPTP) to Relakks using NetworkManager. I can ping server, and connect using same credentials in Windows XP and Vista.

---

