---
title: "Internet problems"
date: 2009-09-26
forum: New to Ubuntu
---

### Post by Nardokor on 2009-09-26
I know it has been brought up before, but none of the threads I found helped.

I am dual booting XP and Ubuntu 8.04 on this computer. Both boot fine, I can use all the applications, but internet won't work on Ubuntu.
I am posting this through XP, so the connection works. I have reinstalled XP several times since the comcast guy set it up, dunno if that is relevant, but it may 
The ISP is comcast.
Linksys modem BFECMU10.
Network adapter is a Realtek RTL8139/810x Family Fast Ethernet NIC.
The DS, US, and online lights remain on with ubuntu, but not ethernet.

Thanks in advance.

---

### Post by halitech on 2009-09-26
what is the output of
```
lspci
```
and
```
sudo ifconfig
```

---

### Post by Nardokor on 2009-09-26
Sorry for the wait.

---

### Post by halitech on 2009-09-26
your adapter is being seen
```
02:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
```
and it does show an IP address
```
eth0      Link encap:Ethernet  HWaddr 00:40:2b:72:2b:b6  
          inet addr:24.21.10.181  Bcast:24.21.15.255  Mask:255.255.248.0
```

so I'm not sure why you can't connect. what do you get when you type in ```
ping google.com
```

---

### Post by Nardokor on 2009-09-27
I get.
```
ping: unknown host google.com
```

I will try another power cycle, but keep it off for about 30 seconds this time.

---

### Post by KIAaze on 2009-09-27
What do you get with:
```
ping 74.125.45.100
```
(one of google's IPs)

If that works, it might be a DNS problem.

Also try to ping the router. Usually its address is 192.168.1.1 or 192.168.2.1. (should be written on it or in the docs)

---

### Post by Nardokor on 2009-09-27
All three give the same message, and it appears to be an infinite loop.

```

PING 74.125.45.100 (74.125.45.100) 56(84) bytes of data.
From 169.254.6.39 icmp_seq=1 Destination Host Unreachable
From 169.254.6.39 icmp_seq=2 Destination Host Unreachable
From 169.254.6.39 icmp_seq=3 Destination Host Unreachable
From 169.254.6.39 icmp_seq=4 Destination Host Unreachable
From 169.254.6.39 icmp_seq=5 Destination Host Unreachable
From 169.254.6.39 icmp_seq=6 Destination Host Unreachable
From 169.254.6.39 icmp_seq=7 Destination Host Unreachable
From 169.254.6.39 icmp_seq=8 Destination Host Unreachable
From 169.254.6.39 icmp_seq=9 Destination Host Unreachable
From 169.254.6.39 icmp_seq=10 Destination Host Unreachable
From 169.254.6.39 icmp_seq=11 Destination Host Unreachable
From 169.254.6.39 icmp_seq=12 Destination Host Unreachable

```

And again, dunno if it is relevant. When I click the icon near the power button to go into manual network setup, the only ones there are wired connection and point to point.

---

### Post by KIAaze on 2009-09-27
This is unlikely, but just to check if you have don't have anything blocked by a firewall:
```
sudo iptables -L
```

By default, it should be something like this:
```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

```

Also, just in case, try:
```
sudo dhclient
```
This should renew the IP address.

Under Windows, did you have to install any special software? Or enter any kind of info?

---

### Post by Nardokor on 2009-09-27
The check for the firewall showed up just like it was supposed to.
The second command brought up this.
```

Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:40:2b:72:2b:b6
Sending on   LPF/eth0/00:40:2b:72:2b:b6
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```And as far as I know, nothing special was installed with windows, and I didn't have to install anything myself. I just reinstalled XP today along with ubuntu, and internet worked fine on XP from the start, without having to configure the connection at all.

Time to get some rest and worry about this tomorrow though.

---

### Post by KIAaze on 2009-09-27
Strange.
Can you try Ubuntu 9.04?

Things to try:
Specify a static IP address. Ideally the same you get under Windows.
GUI:
system>admin>networking

By command-line:
[http://www.ubuntugeek.com/ubuntu-networking-configuration-using-command-line.html](http://www.ubuntugeek.com/ubuntu-networking-configuration-using-command-line.html)
[http://www.ubuntugeek.com/change-ubuntu-system-from-dhcp-to-a-static-ip-address.html](http://www.ubuntugeek.com/change-ubuntu-system-from-dhcp-to-a-static-ip-address.html)

While you're at it, post the contents of "/etc/network/interfaces".
But I don't think I can help you any further.

---

