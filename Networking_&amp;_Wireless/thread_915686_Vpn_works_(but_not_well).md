---
title: "Vpn works (but not well)"
date: 2008-09-10
forum: Networking &amp; Wireless
---

### Post by pir on 2008-09-10
Hi,

Our school works with VPN (Cisco)
I downloaded vpnclient, patched it and installed it, and now it works. 
Until yesterday, my laptop hung after I started firefox.

Today, it works better. I think it is because I patched it ([http://projects.tuxx-home.at/?id=cisco_vpn_client](http://projects.tuxx-home.at/?id=cisco_vpn_client)) .

But now, when I download something (from www or nntp) the system crashes again. The monitor freezes, my mousepointer is nt responding and the capslocklight is flashing.

Who knows the ansfer? :)

(PS: Today I disabled proxy settings in firefox, it might help, I don't know)
(PS2: Sorry for language error's, i am Dutch :P )

Output vpnclient:
[SIZE="1"][INDENT]$ vpnclient connect hsl
Cisco Systems VPN Client Version 4.8.01 (0640)
Copyright (C) 1998-2007 Cisco Systems, Inc. All Rights Reserved.
Client Type(s): Linux
Running on: Linux 2.6.24-19-generic #1 SMP Wed Aug 20 22:56:21 UTC 2008 i686
Config file directory: /etc/opt/cisco-vpnclient

Initializing the VPN connection.
Contacting the gateway at 172.30.16.254
User Authentication for hsl...

The server has requested the following information to complete the user authentication:

Username [s1036814]: 
Password []: 
Authenticating user.
Negotiating security policies.
Securing communication channel.

Your VPN connection is secure.

VPN tunnel information.
Client address: 192.168.32.149
Server address: 172.30.16.254
Encryption: 168-bit 3-DES
Authentication: HMAC-SHA
IP Compression: None
NAT passthrough is inactive
Local LAN Access is disabled[/INDENT][/SIZE]

---

### Post by pir on 2008-09-10
Anyone?

---

