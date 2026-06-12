---
title: "Wireless LTSP Client Not Getting DHCP IP Easily"
date: 2008-05-06
forum: Networking &amp; Wireless
---

### Post by haz2a on 2008-05-06
I have Ubuntu 8.04 LTSP Server working well with wired clients, and now with wireless clients too - but not very conveniently!
I am using two Linksys WAP54G Wireless Access Points in Bridging Mode, one on the LTSP Server wired client network, and one at each wireless client. I was inspired by: [http://wiki.ltsp.org/twiki/bin/view/Ltsp/WirelessLTSPClientsUsingAnEthernetBridge](http://wiki.ltsp.org/twiki/bin/view/Ltsp/WirelessLTSPClientsUsingAnEthernetBridge)

There are 3 main problems in using the wireless client:-

1. After power-cycling the WAP at the client (eg: when switched off overnight) I have to boot Ubuntu first on the client first (eg: 7.10 from hard disk, or possibly from a Live CD [not tried]) - before I can boot via PXE over the wireless bridge. I only have to boot 7.10 to the Recovery Mode command line, then shutdown again. The client can now be booted and rebooted any number of times wirelessly - until the WAP is powered-off again. This doesn't work if I boot Knoppix 5.1.1 either to the cmd line or to the desktop, but Ubuntu 7.10 to either does work.

2. It now takes 2 full cylces of DHCP attempts before the client will start to boot via PXE over the network.
The process, and what appears in /var/log/syslog looks like this:-

 (start the client with hard disk disconnected to boot from network)
 (screen: the 'DHCP...' CLI progress indicator displays one dot for each DHCPDISCOVER/OFFER below:-
May  6 21:30:57 C14 dhcpd: DHCPDISCOVER from 00:1e:8c:7b:b7:60 via eth1
May  6 21:30:57 C14 dhcpd: DHCPOFFER on 192.168.0.39 to 00:1e:8c:7b:b7:60 via eth1
May  6 21:30:59 C14 dhcpd: DHCPDISCOVER from 00:1e:8c:7b:b7:60 via eth1
May  6 21:30:59 C14 dhcpd: DHCPOFFER on 192.168.0.39 to 00:1e:8c:7b:b7:60 via eth1
May  6 21:31:03 C14 dhcpd: DHCPDISCOVER from 00:1e:8c:7b:b7:60 via eth1
May  6 21:31:03 C14 dhcpd: DHCPOFFER on 192.168.0.39 to 00:1e:8c:7b:b7:60 via eth1
May  6 21:31:11 C14 dhcpd: DHCPDISCOVER from 00:1e:8c:7b:b7:60 via eth1
May  6 21:31:11 C14 dhcpd: DHCPOFFER on 192.168.0.39 to 00:1e:8c:7b:b7:60 via eth1
 (screen: No DHCP ... OFFERS ... exiting PXE ROM)
 (pressed spacebar here for second cycle of DHCP attempts)
 ('DHCP....' displayed on screen with no coresponding messages in syslog)
 (finally, about 10 seconds after 4th dot get:- 
May  6 21:32:02 C14 dhcpd: DHCPDISCOVER from 00:1e:8c:7b:b7:60 via eth1
May  6 21:32:02 C14 dhcpd: DHCPOFFER on 192.168.0.39 to 00:1e:8c:7b:b7:60 via eth1
May  6 21:32:18 C14 dhcpd: DHCPREQUEST for 192.168.0.39 (192.168.0.254) from 00:1e:8c:7b:b7:60 via eth1
May  6 21:32:18 C14 dhcpd: DHCPACK on 192.168.0.39 to 00:1e:8c:7b:b7:60 via eth1
May  6 21:32:19 C14 in.tftpd[6367]: tftp: client does not accept options 
May  6 21:32:53 C14 dhcpd: DHCPDISCOVER from 00:1e:8c:7b:b7:60 via eth1
May  6 21:32:53 C14 dhcpd: DHCPOFFER on 192.168.0.39 to 00:1e:8c:7b:b7:60 via eth1
May  6 21:32:53 C14 dhcpd: DHCPREQUEST for 192.168.0.39 (192.168.0.254) from 00:1e:8c:7b:b7:60 via eth1
May  6 21:32:53 C14 dhcpd: DHCPACK on 192.168.0.39 to 00:1e:8c:7b:b7:60 via eth1
May  6 21:32:54 C14 dhcpd: DHCPREQUEST for 192.168.0.39 (192.168.0.254) from 00:1e:8c:7b:b7:60 via eth1
May  6 21:32:54 C14 dhcpd: DHCPACK on 192.168.0.39 to 00:1e:8c:7b:b7:60 via eth1
May  6 21:32:54 C14 nbdrootd[6382]: connect from 192.168.0.39 (192.168.0.39)
May  6 21:32:54 C14 nbd_server[6383]: connect from 192.168.0.39, assigned file is /opt/ltsp/images/i386.img
May  6 21:32:54 C14 nbd_server[6383]: Size of exported file/device is 157556736
May  6 21:33:04 C14 ldminfod[6385]: connect from 192.168.0.39 (192.168.0.39)
 (Client on 192.168.0.39 has now booted over the wireless bridge)

3. Last query: why do I get continued DHCPDISCOVER/OFFER/REQUEST/ACKs between tftpd starting and NBD starting?

Can anyone throw any light on these issues?

---

### Post by haz2a on 2008-05-07
More information:-

Both WAPs have static IPs, as does the server. No encryption is used.

The DHCP messages in syslog show the correct MAC for the interface on the client.

When unable to boot the client, syslog shows that the DHCPDISCOVER is getting through, and DHCPOFFER is being made, but the DHCPOFFER does not get back to the client.

There is no firewall installed on the server (as recommended).

When pressing the spacebar to do the second round of DHCP attempts, it does not matter whether this is done immediately or 10 minutes later, the eventual boot always occurs (when it does succeed) at the same point - after 'DHCP....' with 4 dots (+ 10 seconds). It seems to be a matter of requiring an exact number of attempts rather than an exact time!?

---

