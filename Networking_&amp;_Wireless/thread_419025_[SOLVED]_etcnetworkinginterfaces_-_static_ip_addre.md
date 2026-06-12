---
title: "[SOLVED] /etc/networking/interfaces - static ip address - Linksys BEFSR41"
date: 2007-04-22
forum: Networking &amp; Wireless
---

### Post by altonbr on 2007-04-22
**_Problem_**
I have two servers that need to have static IP addresses assigned to them. I set customize both servers so that their /etc/networking/interfaces file looks like this:

_Server 1_
> auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.1.100
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.1
_Server 2_
> auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.1.101
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.1

I then run
> sudo /etc/init.d/networking restart
and
> sudo dhclient
on both of the servers.

This is what gets returned on the first one:
> bound to 192.168.1.102 -- renewal in 1519964 seconds

I'm using a Linksys BEFSR41 ([http://www.linksys.com/servlet/Satellite?c=L_Product_C2&childpagename=US%2FLayout&cid=1122062340941&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=4094131284B01](http://www.linksys.com/servlet/Satellite?c=L_Product_C2&childpagename=US%2FLayout&cid=1122062340941&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=4094131284B01)) and have tried to configure it so that it doesn't act as a DHCP server (but then dhclient fails). I've tried to get the IP from "Obtain IP Automatically" to "Static IP" but then dhclient fails as well. I've tried setting it so that the first DHCP address is 192.168.1.100 and can only give out 3 addresses, but they never stick to the IP address assigned in /etc/init.d/networking (because it's being assigned an IP via DHCP).

I've tried following this tutorial (even though it's for a Mac), but still no luck: [http://homepage.mac.com/car1son/static_port_fwd_staticip.html](http://homepage.mac.com/car1son/static_port_fwd_staticip.html)

**_Solution?_**
* Can I assign IP addresses via their MAC address? I never saw the option on the UI at 192.168.1.1 though.
* Do I have to install BIND9? I rather do without it. That would be too much to worry about/configure.

How else  can I statically assign IP addresses? Is anyone familar with this router (or how to manage routers in general).This is the most frustrating thing I've encountered thus far.


**_Note_**
I know how to port-forware port 22 and port 80 and all that jazz.

---

### Post by chili555 on 2007-04-22
I think your error is dhclient. That tells networking that you'd like to obtain an IP address from an available DHCP server. That is not what you want. I suggest using```
sudo ifdown eth0
sudo ifup eth0
ping -c3 192.168.1.1
```Then, I believe you will be connected and have the IP address you specified. Post back and let us know.

---

### Post by altonbr on 2007-04-22
Huh. Care to explain what ifdown and ifup do? The name may say it all, but I'll need to know what this does for future reference.

It appeared to work. I ran "ifconfig" and it said I have an IP of "192.168.1.100" just like I stated in /etc/networking/interfaces. Thanks soooo much!

From the man page for "dhclient", I couldn't tell if this was the proper script to run because it was talking about temporary releases, etc. Do you have any information on when "dhclient" should be used?

Thank you so much.

---

### Post by chili555 on 2007-04-22
Well, if you have specified an IP address in /etc/network/interfaces then ifconfig will show an IP address always, whether you are actually linked to the access point or not. The command that tells you for sure is ping. If you can ping the router and [www.google.com](www.google.com), you are hooked up.

Ifup and ifdown merely mean, bring the interface up or down. 

Dhclient should be used to ask a DHCP server, typically a router, for a dynamically assigned, ever changing IP address within the address range specified in the setup pages of the router. If you are going to ssh or ftp into a server, you do not want DHCP, because you will find it difficult, not impossible to find them.

DHCP is perfect for a wireless situation because you fire up your laptop at a motel or coffee shop, get any old IP address and get on the web.

---

### Post by altonbr on 2007-04-22
> **chili555 said:**
> Well, if you have specified an IP address in /etc/network/interfaces then ifconfig will show an IP address always, whether you are actually linked to the access point or not. The command that tells you for sure is ping. If you can ping the router and [www.google.com](www.google.com), you are hooked up.

Ifup and ifdown merely mean, bring the interface up or down. 

Dhclient should be used to ask a DHCP server, typically a router, for a dynamically assigned, ever changing IP address within the address range specified in the setup pages of the router. If you are going to ssh or ftp into a server, you do not want DHCP, because you will find it difficult, not impossible to find them.

DHCP is perfect for a wireless situation because you fire up your laptop at a motel or coffee shop, get any old IP address and get on the web.

Yeah, sorry, I guess I could have just used the man page for that.

Thansk for the info on DHCP/dhclient; it's all coming together now. I was basically trying to assign a static IP while asking for a dynamic one. Whoops.

It's all up and running, so thanks again.

---

