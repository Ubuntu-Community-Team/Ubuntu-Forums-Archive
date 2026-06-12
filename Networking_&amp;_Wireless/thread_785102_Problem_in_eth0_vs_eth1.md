---
title: "Problem in eth0 vs eth1"
date: 2008-05-07
forum: Networking &amp; Wireless
---

### Post by youmee on 2008-05-07
Hi. 

I have 2 network interfaces.

eth0 - onboard nVidia network device.
eth1 - external Realtek device.

Internet interface on eth1. 
    static IP: 10.10.1.4
    broadcast: 255.255.255.0
    gateway: 10.10.1.254
    dns-server: 10.10.1.199
    dns-server2: 10.14.1.199
    p.s. have not DHCP at this network.

ONLY Network interface (i mean localnetwork, share etc) on eth0.
but, DHCP-Server works on this network and dhcp-eth0 overrides my DNS Servers on eth1.

Can anyone help me?

How to fix and configure that?

**eth0** - for network(dhcpclient must receive ONLY: ip,gateway,broadcast)

**eth1** - for Internet(dhcp have not. static ip,broadcast,gateway,dns-servers).

Please help me.

---

### Post by superprash2003 on 2008-05-07
here's how you can configure DNS servers to stick permanently..Opendns servers are used in this guide 208.67.222.222 and 208.67.220.220 you can replace them with what ever you like [http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html](http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html)

---

