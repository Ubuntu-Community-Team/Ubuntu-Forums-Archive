---
title: "Can't change to static IP"
date: 2017-12-27
forum: Networking &amp; Wireless
---

### Post by netsense on 2017-12-27
Hi all,

I'm baffled, trying the change the network interface from a DHCP lease to a static IP. I'm using Linux-Mint 18.3.

I have tried both methods outlines in [https://linuxhint.com/change-from-dhcp- ... ss-ubuntu/]("https://linuxhint.com/change-from-dhcp-to-static-ip-address-ubuntu/"), and the result stubbornly stays on the DHCP-assigned IP.

The current content of my /stc/network/interfaces files is 

[INDENT] interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

# iface dsl-provider inet ppp
# pre-up /sbin/ifconfig --help up # line maintained by pppoeconf
# provider dsl-provider

auto eth0
# iface eth0 inet dhcp
iface eth0 inet static
address 10.1.1.10
netmask 255.0.0.0
gateway 10.1.1.1
dns-nameservers 10.1.1.1 8.8.8.8

[/INDENT]

And  after trying the second method, it appears the network -manager  configuration is lost altogether, and will not accept new connections:  the screenshot of the applet is attached:

---

### Post by netsense on 2017-12-28
Solved.

The answer was a weird one: we had a permanently assigned DHCP address and associated port forward for the box on a Cisco router. It wasn't until after the DHCP assignment on the router was removed that the IP address on the box magically changed. So I'm assuming the Linux box was saying "I want to be 10.1.1.10", and the Cisco box was replying "No, you're 10.1.1.100" and the Linux box was meekly complying. Or some such anthropomorphisation. :)
All good, now

---

