---
title: "Understanding the IP Routing Table"
date: 2007-05-31
forum: Networking &amp; Wireless
---

### Post by icarius on 2007-05-31
I'm a rather noob to linux (and networking in general) and I am trying to understand exactly how to get my machine at work to see my machine at home. I noticed that almost all of my ip addresses are something like 192.168.0.1, how do I know what ip address to enter into a remote machine to make is see a remote machine ? and what exactly is the gateway, broadcast, etc... for. If someone could describe the packet flow or direct me to a networking tutorial, Id greatly appreciate the help.

"Freedom is being free, free to experience the good and the bad"

---

### Post by mbradlcu on 2007-05-31
the questions you're asking can get pretty involved but here's some in a nut shell info.
192.168.0.bla are private network ranges, so in order to see that IP via the web it would need to be either assigned by your ISP or routed through your router, here's an example. My ISP gives currently gives me this IP:
> 76.170.115.194
I'm using an Ubuntu box as a firewall / router / dhcp so the second network card has my private IP:
> 192.168.0.150
all the machines "behind" this box are assigned IP in a range of 192.168.0.100-150. So to connect to my router machine I use the 76.170.115.194 IP... If I want to connect to a machine behind my router machine I have to "forward" the connection port, this is called NAT, network address translation. If you're using a linksys router or somthing like that you'll need to "forward" the connection ports to your machine.
Another cool thing you can do is use a service like no-ip to have an domain name assigned to your IP. mine is qndfix.no-ip.info.. see what I mean by running the following on the command line:
```
host qndfix.no-ip.info
```
lastly, the gateway is the IP for requests that are not on your local network,, so if I request an IP like  64.233.167.99 it's sent on the gateway. the gateway can be seen with this command:
```
route
```
daturan@matt-x64:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     *               255.255.255.0   U     0      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         192.168.0.150   0.0.0.0         UG    0      0        0 eth0
as you can see, requests are sent from this machine to my firewall/router machine.
Hope this helps.

---

