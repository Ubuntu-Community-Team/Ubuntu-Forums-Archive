---
title: "IPtables issue with FTP"
date: 2008-05-06
forum: Networking &amp; Wireless
---

### Post by chrisdavid_175 on 2008-05-06
So I've upgraded my linux pc/router to Ubuntu 8.04 and I can't seem to get it to forward ftp traffic correctly. When used as an ftp server, I can get into it. After configuring iptables to portforward traffic to internal hosts, I can forward ssh, mstsc, vnc, web, and other traffic just fine to exclude ftp.

On the LAN, I can ftp into the ftp server to which the Internet traffic is forwarded without errors (Windows cmd, Windows Explorer, linux terminal). But when I try to FTP to the internal host from the Internet it won't work through Windows Explorer and a another ftp client, Core FTP Lite. However, I can use the Windows cmd line to ftp in just fine. 

The following is my iptables configuration:

#!/bin/bash
#iptables configuration

IPTAB=/sbin/iptables
SERVICE=/sbin/service
lanETH=eth2
wanETH=eth0
lanNET="192.168.15.0/24"

ubuntuS3IP=192.168.15.16

$IPTAB -F
$IPTAB -t nat -F
$IPTAB -t mangle -F
$IPTAB -t nat -A POSTROUTING -s ${lanNET} -o $wanETH -j MASQUERADE
$IPTAB -t nat -A PREROUTING -i $wanETH -p tcp --dport 20 -j DNAT --to-destination $ubuntuS3IP:20
$IPTAB -t nat -A PREROUTING -i $wanETH -p tcp --dport 21 -j DNAT --to-destination $ubuntuS3IP:21

I had been able to forward ftp traffic in the past and use Windows Explorer as the FTP client, but that was with a different distro.

Any ideas?

---

