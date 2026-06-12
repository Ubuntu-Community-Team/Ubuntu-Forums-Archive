---
title: "Cisco VPN on Feisty Fawn"
date: 2007-06-25
forum: Networking &amp; Wireless
---

### Post by jakester03 on 2007-06-25
Ok, so I got logged into the VPN connection just fine:
```

Your VPN connection is secure.

VPN tunnel information.
Client address: <removed for privacy>
Server address: <removed for privacy>
Encryption: 256-bit AES
Authentication: HMAC-SHA
IP Compression: None
NAT passthrough is active on port UDP 4500
Local LAN Access is disabled
```


However,
I cannot ping by hostname nor IP address:
```
jake@ubuntu:~/vpnclient$ ping wspen-it05
ping: unknown host wspen-it05
jake@ubuntu:~/vpnclient$ ping 10.64.14.15
PING 10.64.14.15 (10.64.14.15) 56(84) bytes of data.
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
```

Also, no telnet (times out) and no web browsing... ideas?

---

### Post by tillo on 2007-06-25
You should install network-manager-vpnc, this would help you a lot. Configuration and connection are done through the network manager (double screen icon...).
The "Operation not permitted" problem is probably there because of Firestart: if you use the vpn connection for Internet too, just set the tap interface as the external one. If you don't use the vpn connection for Internet, set the network CIDR on the vpn connection configuration, and deactive Firestart. This works for me.

---

### Post by linuksamiko on 2007-06-27
I have something similar like that. I installed the network-manager-vpnc packeg and I CAN connect to the Cisco-Server BUT I don't have Internet. The route ist setup but nothing happens.
I can't give you more information because I have no idea where to look for anymore.

---

### Post by tillo on 2007-06-29
Paste the result of "route -nv" before and after the connection.

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

