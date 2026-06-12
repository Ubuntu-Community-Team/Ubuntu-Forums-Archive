---
title: "Netgate wireless help"
date: 2007-05-29
forum: Networking &amp; Wireless
---

### Post by atatistcheff on 2007-05-29
I've tried looking through several threads for clues but it looks like I need to post this question.  I have a Dell laptop which has the embedded Broadcom chipset.  Well, I got tired of the ndiswrapper stuff and bought a Netgate CB9 card.  This is supposedly a great chipset for Linux.  Ubuntu recognized the card with no problems however, when trying to connenct to a WPA network it won't successfully negotate a DHCP lease.  I have tried static IPs too and these don't seem to work even though they do show up in ifconfig.  Below are the syslog messges I'm seeing when it tries to get a lease as well as the ifconfig.  Where can I start looking to fix this?

Thanks in advance.

Ifconfig:
ath0      Link encap:Ethernet  HWaddr 00:0B:6B:20:6F:E5
          inet6 addr: fe80::20b:6bff:fe20:6fe5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:387 dropped:0 overruns:0 frame:387
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:200
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:177 Memory:f8b60000-f8b70000

syslog:
May 29 12:59:09 localhost dhclient: DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 9
May 29 12:59:18 localhost dhclient: DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 15
May 29 12:59:33 localhost dhclient: DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 12
May 29 12:59:45 localhost dhclient: DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 13
May 29 12:59:58 localhost dhclient: No DHCPOFFERS received.
May 29 12:59:58 localhost dhclient: No working leases in persistent database - sleeping.
May 29 13:02:58 localhost dhclient: DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 3
May 29 13:03:01 localhost dhclient: DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 6
May 29 13:03:07 localhost dhclient: DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 6
May 29 13:03:13 localhost dhclient: DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 10
May 29 13:03:23 localhost dhclient: DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 20
May 29 13:03:43 localhost dhclient: DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 16
May 29 13:03:59 localhost dhclient: No DHCPOFFERS received.
May 29 13:03:59 localhost dhclient: No working leases in persistent database - sleeping.
May 29 13:04:20 localhost gconfd (root-4934): GConf server is not in use, shutting down.
May 29 13:04:20 localhost gconfd (root-4934): Exiting

---

