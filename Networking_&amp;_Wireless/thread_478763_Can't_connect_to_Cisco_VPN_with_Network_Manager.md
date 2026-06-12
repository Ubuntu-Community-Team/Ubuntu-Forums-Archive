---
title: "Can't connect to Cisco VPN with Network Manager"
date: 2007-06-19
forum: Networking &amp; Wireless
---

### Post by ebeyer on 2007-06-19
I've been trying with little success to connect to the VPN we have at work using the VPN clients I have on my x86 linux (Ubuntu Feisty v7.04) client. Our IT department has me using the prorpietary Cisco client for Mac OS X which works just fine and uses the same home network the linux box does.

When trying to connect via Network manager, I get a connection error.

I have moved over the .pcf to the linux box and am using the exact same user name and password the Mac client is using. However, whenever I try to connect I get:

eric@frank:/etc/init.d$ vpnclient connect cmg
Cisco Systems VPN Client Version 4.8.00 (0490)
Copyright (C) 1998-2005 Cisco Systems, Inc. All Rights Reserved.
Client Type(s): Linux
Running on: Linux 2.6.20-06-generic #2 SMP Thu Jun 7 20:19:32 UTC 2007 i686
Config file directory: /etc/opt/cisco-vpnclient

privsep: unable to drop privileges: group set failed.
The application was unable to communicate with the VPN sub-system.
eric@frank:/etc/init.d$

I have similar frustrations with kVPNC.

Network security is not one of my skills. Any guidance as to how to proceed from here would be truly appreciated.

EB

---

### Post by GrumpyBob on 2007-06-21
I have used vpnc with network manager to connect successfully with my work vpn, which is Cisco.  Unfortunately they are switching from a system using an RSA SecurID digital token (which works fine) to an Entrust system, which I cannot get to work.

Incidentally, installing the Cisco client 4.8 required a patch for the latest kernel.

Robert

---

### Post by sunken on 2007-07-15
ok, I did like this:
Text in *italic* is yours to find out

[LIST=1]
[*]install vpnc with synaptic
[*]open terminal, type **sudo pico /etc/vpnc/default.conf**
An example of default.conf:
[B]IPSec gateway *ip.to.vpn.server*
IPSec ID *VPNservergroupname*
IPSec obfuscated secret *cryptedpasswordfrompcffile*
Xauth interactive[/B]
[*]**ctrl+x**
[*]**y**
[*]**sudo vpnc-connect**
[*]enter your vpn user name, **enter**
[*]enter pin code or what ever kind of system you have, **enter**. Now you're inside vpn tunnel
[*]after you're done, **sudo vpnc-disconnect**
[/LIST]

---

