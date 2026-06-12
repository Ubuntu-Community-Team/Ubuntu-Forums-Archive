---
title: "Help with PPTPD with VPS Server.  Windows clients getting defult gateway of 0.0.0.0"
date: 2013-12-27
forum: Networking &amp; Wireless
---

### Post by nikonzero on 2013-12-27
Hi,

Recently purchased a VPS to use as a VPN server, and installed PPTPD to allow this.  I probably know just enough about Linux to get myself into trouble, so I'm throwing myself upon the mercy of those with more skill to hopefully help me out.

I am able to connect to the VPN from different locations (different ISP's, routers, etc), however always get a default gateway of 0.0.0.0, which limits what it's useful for.  I need to use the VPN so that all traffic routes from the Windows clients, via the server, to the destination.

Below I'm attaching the content of the configuration files, and hopefully someone will be able to see why I'm having the trouble.  Please note that xx.xx.xx.xx represents my public IP address on the server box in all cases.  Any help you can lend would be greatly appreciated.

ifconfig

```
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:74 errors:0 dropped:0 overruns:0 frame:0
          TX packets:74 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:4424 (4.4 KB)  TX bytes:4424 (4.4 KB)
ppp0      Link encap:Point-to-Point Protocol
          inet addr:xx.xx.xx.xx  P-t-P:10.1.0.1  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1396  Metric:1
          RX packets:504 errors:0 dropped:0 overruns:0 frame:0
          TX packets:536 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3
          RX bytes:60417 (60.4 KB)  TX bytes:204009 (204.0 KB)
ppp1      Link encap:Point-to-Point Protocol
          inet addr:xx.xx.xx.xx  P-t-P:10.1.0.2  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1396  Metric:1
          RX packets:412 errors:0 dropped:0 overruns:0 frame:0
          TX packets:101 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3
          RX bytes:85080 (85.0 KB)  TX bytes:20275 (20.2 KB)
venet0    Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00
          inet addr:127.0.0.2  P-t-P:127.0.0.2  Bcast:0.0.0.0  Mask:255.255.255.255
          UP BROADCAST POINTOPOINT RUNNING NOARP  MTU:1500  Metric:1
          RX packets:3270 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3284 errors:0 dropped:2 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:824750 (824.7 KB)  TX bytes:730381 (730.3 KB)
venet0:0  Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00
          inet addr:xx.xx.xx.xx  P-t-P:xx.xx.xx.xx  Bcast:xx.xx.xx.xx  Mask:255.255.255.255
          UP BROADCAST POINTOPOINT RUNNING NOARP  MTU:1500  Metric:1

```

Windows client ipconfig for VPN

```
PPP adapter VPN:
   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : VPN
   Physical Address. . . . . . . . . :
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes
   IPv4 Address. . . . . . . . . . . : 10.1.0.1(Preferred)
   Subnet Mask . . . . . . . . . . . : 255.255.255.255
   Default Gateway . . . . . . . . . : 0.0.0.0
   DNS Servers . . . . . . . . . . . : 8.8.8.8
                                       8.8.4.4
   NetBIOS over Tcpip. . . . . . . . : Enabled

```
```


/etc/ppp/pptpd-options

name pptpd
refuse-pap
refuse-chap
refuse-mschap
require-mschap-v2
require-mppe-128
ms-dns 8.8.8.8
ms-dns 8.8.4.4
proxyarp
nodefaultroute
lock
nobsdcomp
```

/etc/pptpd.conf


```
option /etc/ppp/pptpd-options
logwtmp
localip xx.xx.xx.xx
remoteip 10.1.0.1-100
```

/etc/rc.local

```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
iptables -P FORWARD ACCEPT
iptables -t -nat -A POSTROUTING -o venet0:0 -j MASQUERADE
exit 0


```

Any help you are able to lend would be appreciated.

---

### Post by SeijiSensei on 2013-12-28
Did you enable packet forwarding in /etc/sysctl.conf?  [Read this](https://help.ubuntu.com/community/PPTPServer) for details.

I don't think the default gateway is the problem.  I didn't see it specified in that documentation.  After masquerading, the PPP connections will use the server's default gateway.

Also that documentation uses iptables to [resize]("http://www.linuxtopia.org/Linux_Firewall_iptables/x4700.html") the TCP packets being transported by PPP.

---

### Post by nikonzero on 2013-12-28
Hi Seijisensei,

I actually used that guide first to set up the service. :)  I since used an automated script to be absolutely certain the config was correct.  I can confirn I have definitely allowed forwarding.

---

