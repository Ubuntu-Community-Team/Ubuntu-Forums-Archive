---
title: "Network Manager and VPN"
date: 2021-05-25
forum: Networking &amp; Wireless
---

### Post by kupnu42605 on 2021-05-25
The problem I have is that VPN connections set up in NM don't provide the access to VPN internal sites.


I tried to set up FortiNet VPN and L2TP. I see no errors, and the  status is Connected. Though, when I open an internal site in any browser  (like utiv01.oua.internal), the server is not found. I have all the  needed NM modules installed.

 
When I use openfortivpn for the Forti VPN connection from the CLI, all works fine.

 
I have already tried DNS resolution with dnsmasq according to ArchWiki, but no success.

 
I use KDE, so configured NM using its Plasma applet.

 
Please, help, I'm a newbie in networking, so could have provided not enough information.

---

### Post by TheFu on 2021-05-25
Don't know anything about FortiNet. Sorry. I don't use network-manager - actually purge it from my systems since it seems to get confused when non-trivial networking is used. 

To my knowledge, whether a split tunnel is allowed is controlled by the VPN server configuration. In a corporate environment, we usually do not allow split tunnels.  This prevents printing or seeing any local devices on the LAN. It is a security thing.  Allowing a client to control the split-tunnel or not would be a completely security failure. I've not seen that allowed. The settings are on the server-side, in the setup for each connection group.

If the same client config file and client authentication credentials are being used for each VPN connection, I don't see how the connection, split-tunnel or not, could be different.

Perhaps check the routing table?  **route -n** is the command that makes the prettiest output.  Look at the 3 different situations:
[LIST]
[*]Before any VPN connection
[*]After the CLI VPN connection
[*]After the NM-GUI VPN connection
[/LIST]

You can also check the actual program and options being used by looking at the complete process table.  Compare those between the 2 VPN connections. What's different?

---

### Post by kupnu42605 on 2021-05-27
Sorry for a rather long reply. Here I provide ```
route -n
``` for the **FortiNet** VPN:

**Before any connection:**

```
$ sudo route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 enp1s0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 enp1s0
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 enp1s0
```

**CLI:**

```
$ sudo openfortivpn vpn.***.com.au -u ***

$ sudo route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 enp1s0
10.0.0.0        0.0.0.0         255.255.255.0   U     0      0        0 ppp0
10.1.1.0        0.0.0.0         255.255.255.0   U     0      0        0 ppp0
10.10.7.0       0.0.0.0         255.255.255.0   U     0      0        0 ppp0
125.7.41.164    192.168.0.1     255.255.255.255 UGH   0      0        0 enp1s0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 enp1s0
192.0.2.1       0.0.0.0         255.255.255.255 UH    0      0        0 ppp0
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 enp1s0
192.168.1.64    0.0.0.0         255.255.255.192 U     0      0        0 ppp0
192.168.7.0     0.0.0.0         255.255.255.0   U     0      0        0 ppp0
192.168.8.0     0.0.0.0         255.255.255.0   U     0      0        0 ppp0
192.168.18.0    0.0.0.0         255.255.255.0   U     0      0        0 ppp0
192.168.202.0   0.0.0.0         255.255.255.128 U     0      0        0 ppp0
192.168.211.0   0.0.0.0         255.255.255.128 U     0      0        0 ppp0
```

**NM:**

```
sudo route -n 
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 enp1s0
0.0.0.0         0.0.0.0         0.0.0.0         U     50     0        0 ppp0
0.0.0.0         192.168.0.1     0.0.0.0         UG    100    0        0 enp1s0
10.0.0.0        10.0.1.1        255.255.255.0   UG    50     0        0 ppp0
10.1.1.0        10.0.1.1        255.255.255.0   UG    50     0        0 ppp0
10.10.7.0       10.0.1.1        255.255.255.0   UG    50     0        0 ppp0
125.7.41.164    192.168.0.1     255.255.255.255 UGH   100    0        0 enp1s0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 enp1s0
192.0.2.1       0.0.0.0         255.255.255.255 UH    50     0        0 ppp0
192.168.0.0     0.0.0.0         255.255.255.0   U     100    0        0 enp1s0
192.168.0.1     0.0.0.0         255.255.255.255 UH    100    0        0 enp1s0
192.168.1.64    10.0.1.1        255.255.255.192 UG    50     0        0 ppp0
192.168.7.0     10.0.1.1        255.255.255.0   UG    50     0        0 ppp0
192.168.8.0     10.0.1.1        255.255.255.0   UG    50     0        0 ppp0
192.168.18.0    10.0.1.1        255.255.255.0   UG    50     0        0 ppp0
192.168.202.0   10.0.1.1        255.255.255.128 UG    50     0        0 ppp0
192.168.211.0   10.0.1.1        255.255.255.128 UG    50     0        0 ppp0

```

In case I use the CLI, the connection works perfectly, and when I use NM, I can't reach internal remote sites.
In both cases regular sites are loaded as appropriate.

---

### Post by TheFu on 2021-05-27
So, what's different?  This is your task to determine.  I would put the NM output in to 1 file and the CLI output into another file, then use a file comparison tool to show the difference.  **meld** is my diff tool of choice, but diff, sdiff, or any of the 50 others can work. Whatever you like.  Meld is quite excellent.

---

### Post by kupnu42605 on 2021-05-28
So, the outputs are totally different. What can I do with this?

---

### Post by TheFu on 2021-05-28
Figure out what makes them different and "convince" the one that doesn't work the way you like to be more like the other?  

Look at the differences closer. One has a gateway and different metric values.

---

### Post by kupnu42605 on 2021-05-28
Okay. I'll try to know about it a bit more. Thanks!

---

### Post by kupnu42605 on 2021-05-28
Don't the both cases have gateway? How can you determine if a connection has a gateway?

---

### Post by TheFu on 2021-05-28
You'll need to understand the output from those commands better to solve this. I can only suggest reading the manpage for the commands used and looking through the explanation for the output columns, then looking up what each means.  Best to use the manpage for the command that is ALREADY on your system.

Look at the gateways and the metrics.  Then you can try to figure out why fortinet startup isn't using the same config file on each side - or what network-manager is breaking.  I don't know fortinet or network-manager.  Sorry.  I start my VPN(s) from the shell, always, using sudo.  I don't have a VPN enabled always, except on a wifi tablet.  All the other devices use a VPN only when needed.

---

### Post by kupnu42605 on 2021-06-18
The solution may be found here:

[https://www.linuxquestions.org/questions/linux-networking-3/debian-11-network-manager-and-vpn-sites-don%27t-open-4175695571/](https://www.linuxquestions.org/questions/linux-networking-3/debian-11-network-manager-and-vpn-sites-don%27t-open-4175695571/)

---

### Post by TheFu on 2021-06-18
Glad you figured this out.
ifupdown and /etc/network/interfaces has been deprecated on Ubuntu for a few years.  Ubuntu moved to Netplan.  BTW, Debian is **not** an official flavor of ubuntu.  Would have been better to place this question into the Debian sub-forum.  Seems in the LinuxQuestions link, someone with the same username as here said Debian was being used. That could have helped someone else know the specific differences between debian and Ubuntu network stacks.

For lurkers, if you have any networking issue, the first steps are to test ping using IP addresses and using DNS names. If IP works, but DNS doesn't, you know that DNS is the problem and can concentrate on that.  If IPs don't ping, then the problem becomes much more complex.

I find it odd that the DNS worked from the CLI - managed by network manager, but not from the GUI network-manager.  That doesn't make sense. Seems like a bug.  On all the VPNs I've used and manage, we (on the VPN server side) always forced the correct DNS for every client.  Clients should never need to know a DNS setting. The VPN should pass that in the connection configuration automatically and it should override any localized settings.  Anything less is a bug, IMHO.

---

