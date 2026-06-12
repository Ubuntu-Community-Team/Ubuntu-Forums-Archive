---
title: "VPNC connected but no inbound traffic"
date: 2007-06-19
forum: Networking &amp; Wireless
---

### Post by bthawabi on 2007-06-19
My problem is that I have managed to successfully establish a VPN connection to my work network using VPNC. Right after the connection is established, I am unable to connect to anything, neither on or out of the remote network.

My ifconfig output for the tun0 is as follows

```
tun0      Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  
          inet addr:192.168.194.23  P-t-P:192.168.194.23  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1390  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:48 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:0 (0.0 b)  TX bytes:3456 (3.3 KiB)
```

The IP address shown above is different from my eth0 IP address (192.168.0.104). You can see how this interface has transmitted 48 packets but did not receive a single one.

Furthermore, my IP route after connecting is:

```

<DNS1 IP> dev tun0  scope link 
<DNS2 IP> dev tun0  scope link 
<VPN Server IP> via 192.168.0.1 dev eth0  src 192.168.0.104  mtu 1500 advmss 1460
192.168.0.0/24 dev eth0  proto kernel  scope link  src 192.168.0.104 
199.253.64.0/23 dev tun0  scope link 
165.177.0.0/16 dev tun0  scope link 
169.242.0.0/16 dev tun0  scope link 
169.254.0.0/16 dev eth0  scope link  metric 1000 
22.0.0.0/8 dev tun0  scope link 
25.0.0.0/8 dev tun0  scope link 
45.0.0.0/8 dev tun0  scope link 
default via 192.168.0.1 dev eth0 

```

Any insight about this problem is highly appreciated. Thank you

---

### Post by bthawabi on 2007-06-21
I have done further testing. Disabling the firewall did not resolve this issue. Also, looking at the different interfaces, i saw my eth0 interface sending out data to the VPN gateway but no responses were coming back.

---

