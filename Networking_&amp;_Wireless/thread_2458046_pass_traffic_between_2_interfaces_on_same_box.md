---
title: "pass traffic between 2 interfaces on same box"
date: 2021-02-15
forum: Networking &amp; Wireless
---

### Post by tempestuous on 2021-02-15
Hello.  I'm asking for some networking expertise, please.
I have set up a small DLNA server, on a NanoPi NEO3, running Ubuntu Core 18.04.
On the NEO3 I have successfully set up the DLNA server (minidlna), samba, a wifi interface, an ethernet interface, and a DHCP server running on the ethernet interface.
The ethernet interface is connected to the DLNA endpoint device (an Audio Pro C5).  I have set a static IP address for this interface of 10.0.0.1, and its DHCP server hands out IP address 10.0.0.2 to the DLNA endpoint device.

The NEO3's wifi interface is configured to connect to my home router, with a static IP address of 192.168.1.102.
I'm running a DLNA controller app (BubbleUPnP) on my Android phone, connected to this same wifi router.

So far, so good.  The stumbling block is that I need to pass network traffic between the two interfaces (eth0 and wlan0) of my NEO3 for this to all work.  After reading many HOWTO's on the web, I tried two different approaches:

i) creating static routes with "ip route"
```
sudo ip route add 10.0.0.0/24 via 192.168.1.102 dev wlan0
sudo ip route add 192.168.1.0/24 via 10.0.0.1 dev eth0
```

then added this to /etc/sysctl.conf
```
net.ipv4.ip_forward=1
```

ii) Network Address Translation with iptables
```
sudo iptables -A FORWARD -i eth0 -j ACCEPT
sudo iptables -A FORWARD -i wlan0 -j ACCEPT
sudo iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
sudo iptables -t nat -A POSTROUTING -o wlan0 -j MASQUERADE
```

In both cases, from my phone (or any other device on the 192.168.1.x network) I could not ping 10.0.0.1.
Can anyone please tell me which way to go with this?
Thanks.

---

