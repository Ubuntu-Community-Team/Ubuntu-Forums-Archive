---
title: "Passing VPN Traffic to another interface."
date: 2015-05-09
forum: Networking &amp; Wireless
---

### Post by shaunnevi on 2015-05-09
Hi Guys

I have a PPTP Server setup,I followed the instruction here [https://help.ubuntu.com/community/PPTPServer](https://help.ubuntu.com/community/PPTPServer)
I have 2 NICs on this machine, on eth0 I am  connected to  my WAN side which allows for the
PPTP clients to dial in.The other interface connects to a switch of an internal network.

I followed the instruction here to have traffic routed between my 2 interfaces [http://ubuntuforums.org/showthread.php?t=1905048](http://ubuntuforums.org/showthread.php?t=1905048)

My problem is that the VPN clients when connected are not able to access any of the machines on the internal network,connected on eth1.

Please let me know how to achieve this please.

Thanks
Shaun

---

### Post by SeijiSensei on 2015-05-09
I'm afraid the advice given in that thread doesn't survive a reboot.  To permanently enable packet forwarding in the kernel, use the command "sudo nano /etc/sysctl.conf".  Remove the hash mark ("#") from the line that reads "net.ipv4.ip_forward=1", save the file with Ctrl+S, then exit with Ctrl+X.  Reboot.  Can they connect now?

---

### Post by shaunnevi on 2015-05-09
> **SeijiSensei said:**
> I'm afraid the advice given in that thread doesn't survive a reboot.  To permanently enable packet forwarding in the kernel, use the command "sudo nano /etc/sysctl.conf".  Remove the hash mark ("#") from the line that reads "net.ipv4.ip_forward=1", save the file with Ctrl+S, then exit with Ctrl+X.  Reboot.  Can they connect now?

Thanks,but I had already done this, it is part of the PPTP Server setup.

---

### Post by SeijiSensei on 2015-05-09
Show us the contents of "route -n" with a couple of remote connections active.

---

### Post by shaunnevi on 2015-05-10
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         0.0.0.0         0.0.0.0         U     0      0        0 ppp0
10.0.3.0        0.0.0.0         255.255.255.0   U     9      0        0 wlan0
192.168.0.189   0.0.0.0         255.255.255.255 UH    0      0        0 ppp0


It is almost as if the traffice seems to get there but it does not know how to come back to the VPN client.

---

### Post by shaunnevi on 2015-05-10
From VPN client

```

Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         0.0.0.0         0.0.0.0         U     0      0        0 ppp0
10.0.3.0        0.0.0.0         255.255.255.0   U     9      0        0 wlan0
192.168.0.189   0.0.0.0         255.255.255.255 UH    0      0        0 ppp0

```

From Server

```

Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.190   0.0.0.0         255.255.255.255 UH    0      0        0 ppp0
192.168.5.0     0.0.0.0         255.255.255.0   U     0      0        0 eth1
192.168.99.0    192.168.5.9     255.255.255.0   UG    0      0        0 eth1
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.0.200   0.0.0.0         UG    100    0        0 eth0
```

It is almost as if the packet does not know how to come back to the client.

---

### Post by SeijiSensei on 2015-05-11
You need to use an entirely different subnet for the ppp0 interface.  The 192.168.0.0/24 network uses the Ethernet so packets intended for a PPP client in 192.168.0.0/24 are sent out eth0. Give the remotes addresses in another subnet like 192.168.50.0/24.  The Ubuntu box will handle routing between the PPP and Ethernet networks.

---

