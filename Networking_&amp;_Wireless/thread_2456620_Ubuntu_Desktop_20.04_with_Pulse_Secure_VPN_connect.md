---
title: "Ubuntu Desktop 20.04 with Pulse Secure VPN connected does not pass data"
date: 2021-01-15
forum: Networking &amp; Wireless
---

### Post by SynUK on 2021-01-15
Hi,

Not sure what I am doing wrong ....

I have a nice clean install of Ubuntu Desktop 20.04. 

I have installed and configured the Pulse Secure VPN client onto it as used by my company.

The VPN client connects with no problems and I get a new network interface called tun0.

The problem is that nothing I then try to connect to on the other end of the VPN is available. I cant connect to my company proxy, the DNS servers or any machine on the company network.

Am I doing something really stupid or should the VPN connection take care of all the network routing on the Ubuntu client ?

Thanks.

Dean.

---

### Post by TheFu on 2021-01-17
The VPN server should provide correct routing and DNS for the connection to work to internal systems.
Browsing a network often doesn't work on older Windows networks. But if you know the exact IP addresses then those connections should work.  If so, you know it is just dns. 

It really would help to see the network connections with and without the VPN active.
```
route -n
ip a
```
and the dns settings.  Those are in /etc/resolv.conf and change when the vpn is active.

It is likely you'll have to get the vpn server guys to make changes. Providing that information above should be all they need.

---

