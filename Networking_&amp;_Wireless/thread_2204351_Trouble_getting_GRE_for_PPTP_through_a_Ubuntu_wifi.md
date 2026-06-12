---
title: "Trouble getting GRE for PPTP through a Ubuntu wifi access point"
date: 2014-02-08
forum: Networking &amp; Wireless
---

### Post by kenmcd on 2014-02-08
I have a Ubuntu box acting as a wifi access point, with a usb-based wireless broadband connection to the Internet.

Connections to the Ubuntu box over wifi and to the Internet beyond are fine for http, ssh, ftp, etc. from Windows, Linux and Android hosts.  So far so good.

But I have a Windows 7 box that needs to establish a Windows PPTP VPN connection passing through the Ubuntu box and this does not work ... it starts the connection protocol (so I can get some packets through) but then hangs.

I know this is NOT a Windows VPN config problem, because if I connect the same wireless broadband connection directly to the Windows machine, the VPN connection works like a charm.

Happy to provide any additional information that might be useful, but I'm stumped at the moment.

---

### Post by tomearp on 2014-02-08
Do you have a firewall configured on the Ubuntu machine? If so, please paste the outputs of
```
sudo iptables -L -n -v
```
and
```
sudo iptables -t nat -L -n -v
```

---

### Post by kenmcd on 2014-02-08
> **tomearp said:**
> Do you have a firewall configured on the Ubuntu machine? 

Nothing special just ip_forward=1 in /proc/sys/net/ipv4 and simple masquerading (as suggested at [http://askubuntu.com/questions/180733/how-to-setup-a-wi-fi-hotspot-access-point-mode](http://askubuntu.com/questions/180733/how-to-setup-a-wi-fi-hotspot-access-point-mode))

> If so, please paste the outputs of ...

```

$ sudo iptables -L -n -v
Chain INPUT (policy ACCEPT 695 packets, 103K bytes)
 pkts bytes target     prot opt in     out     source               destination 


Chain FORWARD (policy ACCEPT 2997 packets, 1013K bytes)
 pkts bytes target     prot opt in     out     source               destination 


Chain OUTPUT (policy ACCEPT 502 packets, 82058 bytes)
 pkts bytes target     prot opt in     out     source               destination 

$ sudo iptables -t nat -L -n -v
Chain PREROUTING (policy ACCEPT 480 packets, 68120 bytes)
 pkts bytes target     prot opt in     out     source               destination 


Chain INPUT (policy ACCEPT 25 packets, 3769 bytes)
 pkts bytes target     prot opt in     out     source               destination 


Chain OUTPUT (policy ACCEPT 111 packets, 8724 bytes)
 pkts bytes target     prot opt in     out     source               destination 


Chain POSTROUTING (policy ACCEPT 111 packets, 8724 bytes)
 pkts bytes target     prot opt in     out     source               destination 
    0     0 MASQUERADE  all  --  *      wwan0   10.10.0.0/16         0.0.0.0/0  
  256 15015 MASQUERADE  all  --  *      ppp0    10.10.0.0/16         0.0.0.0/0  



```

---

### Post by tomearp on 2014-02-09
That seems fair enough, if you were making use of the filter tables then you would need a rule for GRE.

The USB based wireless broadband connection: is that a '3G dongle' or similar? If so, which network are you on?

The reason I ask is that a few years ago I worked for a company that provided mobile broadband dongles for employees who needed remote access. They were on the O2 network. The Windows software that was supplied with the dongle allowed different modes of operation.

In its 'normal' mode I could surf, use SSH etc. incidentally I could use the company VPN as it was an SSL VPN using port 443 so it just appeared as though I was connected to a secure website. However I could not access customer sites over PPTP or L2TP/IPsec VPNs.

The dongle also had a VPN mode. It used the same APN setting with a different username and password. This mode would allow only VPN connections to be made, no browsing, or SSL VPN etc. Obviously once connected to a VPN you could then browse through the remote gateway, at the expense of whoever's network it was.

From speaking to the mobile network's technical team the idea behind this mode was to restrict employees, forcing them to connect to a company VPN with PPTP or L2TP/IPsec so all their traffic is routed through that and can be monitored etc.

So it may be that your dongle doesn't support VPN pass-thru by default.

---

### Post by kenmcd on 2014-02-09
I don't believe it is the dongle as it does not have any visible option in the UI on either platform.

But here are the details [http://www.internode.on.net/support/guides/internet_access/nodemobile_data/huawei_e3131_3g_modem/](http://www.internode.on.net/support/guides/internet_access/nodemobile_data/huawei_e3131_3g_modem/)

---

### Post by tomearp on 2014-02-09
Sorry, yes the dongle shouldn't be the issue, and I just read in the OP that you say the dongle plugged into the Win7 box is working fine.

---

### Post by tomearp on 2014-02-09
Just been having a scout around and there is some suggestion that [loading an additional module]("http://fixunix.com/networking/548231-nat-routing-gre.html") for iptables might be necessary to allow connection tracking to work correctly with GRE:
```
sudo modprobe ip_nat_pptp
```

---

