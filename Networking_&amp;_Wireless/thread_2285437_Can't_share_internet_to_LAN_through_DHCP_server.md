---
title: "Can't share internet to LAN through DHCP server"
date: 2015-07-06
forum: Networking &amp; Wireless
---

### Post by austin38 on 2015-07-06
So I'm new to Ubuntu forums and networking in general. I've asked a few questions on AskUbuntu.com on this topic but for some reason, none of my questions have attracted any responses. This is pretty much a duplicate of my askubuntu question found [here]("http://askubuntu.com/questions/644191/configure-dhcp-on-ubuntu-12-04-to-share-internet-to-subnet").

So here's my problem:

I have 11 computers running Ubuntu 12.04. One computer (I'll refer to this one as prefect), which has two network cards configured, is connected to the internet. The other 10 are connected in a LAN which is connected to the prefect. Currently, the 10 computers in a LAN cannot ping an external IP's but I can ping prefect or any other computer in the LAN. To share the internet through prefect to the LAN clients, I decided to configure a dhcp server on prefect. I've tried a number of different approaches but nothing to seems to work.

**This is what I've done so far.**

I've edited my /etc/network/interfaces

```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet static
        address 192.168.1.100
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255
```

Edited my rc.local

```
/sbin/iptables -P FORWARD ACCEPT
/sbin/iptables --table nat -A POSTROUTING -o eth0 -j MASQUERADE       
exit 0
```

and edited my /etc/dhcp/dhcpd.conf

```
ddns-update-style none;

option domain-name "example.org";
option domain-name-servers ns1.example.org, ns2.example.org;

default-lease-time 86400;
max-lease-time 604800;

authoritative;

log-facility local7;

subnet 192.168.1.0 netmask 255.255.255.0 {
        range 192.168.1.1 192.168.1.10;
        option subnet-mask 255.255.255.0;
        option broadcast-address 192.168.1.255;
        option routers 192.168.1.100;
}
```

**Some helpful information.**

prefect IP: 128.2.218.180
Client IP's: 192.168.1.1-10

ifconfig

```
eth0      Link encap:Ethernet  HWaddr ...  
          inet addr:128.2.218.180  Bcast:128.2.219.255  Mask:255.255.254.0
          inet6 addr: ...

eth1      Link encap:Ethernet  HWaddr ...  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: ...
```

ip route show

```
128.2.218.0/23 dev eth0  proto kernel  scope link  src 128.2.218.180 
169.254.0.0/16 dev eth1  scope link  metric 1000 
192.168.1.0/24 dev eth1  proto kernel  scope link  src 192.168.1.100
```

After doing all of this, I am still can't get the clients to ping any IP's outside of the LAN. Have I overlooked something? Are there any typo's I overlooked? I aslo don't have a good grasp on the different configuration settings for the dhcpd.conf file, is everything correct there?

Any suggestions are more than appreciated and please feel free to ask for more information if needed.

Thanks in advance!

---

### Post by TheFu on 2015-07-06
DHCP just provides network settings to clients. It doesn't replace routing.
It isn't clear what you've setup where in the post above - please **CLEARLY label** the outputs from each command for which machine(s) it is from.

On the "router", you must enable routing (i.e. *ipv4 forwarding*). [https://askubuntu.com/questions/311053/how-to-make-ip-forwarding-permanent](https://askubuntu.com/questions/311053/how-to-make-ip-forwarding-permanent) That is a kernel setting and has security implications to be aware. 

Most people would dedicate a system just for this purpose and they would load a router/firewall-specific distro to prevent most noob-ish networking mistakes that are likely. Heck - I've been doing this stuff for over 20 yrs and I would not try to create my our router with a stock Ubuntu.   Something like Smoothwall [http://www.smoothwall.org/](http://www.smoothwall.org/) or pfsense [https://www.pfsense.org/](https://www.pfsense.org/) are fairly easy to setup and do most of the correct things by default. That's good for the network security.

I would STRONGLY recommend you go with the router distro solution and not attempt to reinvent the wheel.

---

### Post by SeijiSensei on 2015-07-06
Look in /etc/sysctl.conf and make sure the line
```
net.ipv4.ip_forward=1
```
is not commented out with a hash mark at the front of the line.  If it is, remove the hash mark and reboot.

By default Ubuntu will not forward packets across interfaces for security reasons.

---

### Post by austin38 on 2015-07-06
@TheFu
Sorry, I should have mentioned that all of the output above is for prefect. Other than IP configuration (letting the clients and prefect ping each other) , nothing else has been touched on the client machines. Would you like to see client settings/do I need to configure anything on the client end?

You are right about security. From everything I've read, it's child's play to hack a system using dhcp with no firewall. I am definitely willing to explore other alternatives to dhcp. I tried sharing internet to the clients initially through configuring NAT with iptables, following [this tutorial]("http://xmodulo.com/internet-connection-sharing-iptables-linux.html"), but it didn't work leading me to explore dhcp. It's possible I made mistakes leading it to not work.

@SeijiSensei & @TheFu
I forgot to mention that I had enabled ipv4 packet forwarding in the sysctl.conf file. With that in mind and understanding this isn't a secure approach, what else would be keeping this from not working?

Also, I'm very open to other options by the way. Is  there a way to do this without using a dhcp server that would also be  secure? I would like to avoid adding hardware but if that's the only  option I can get to work then so be it.

Thanks guys!

---

