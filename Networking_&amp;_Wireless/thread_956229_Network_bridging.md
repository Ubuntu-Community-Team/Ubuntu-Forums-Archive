---
title: "Network bridging"
date: 2008-10-23
forum: Networking &amp; Wireless
---

### Post by BionicSniper on 2008-10-23
I am setting up a server in my dorm (i'm a student at iowa state university) and i need it to forward it's inet to my router. It has to be this way as my server gets a hostname as long as it is infront of my router

so the physical network topography will be wall->server->router->other stuff

I have the actual internet going into eth0 which is the onboard nic then i have it bridged to eth1 and then a cable going from eth1's nic card to my router (this is what isn't working yet. and i would perferably have it going into the wan port)

i am running the newest version of ubuntu server 8.04 (2.6.24-21 i believe).

heres my /etc/network/interfaces
```
auto lo
iface lo inet loopback

# onboard nic
auto eth0
iface eth0 inet dhcp

# pci nic
auto eth1
iface eth1 inet static
address 192.168.1.12
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255

# Bridge
auto br0
iface br0 inet dhcp
brige_ports eth0 eth1

```

i'm not sure if the bridge stuff is doing anything though. Any ideas?

---

### Post by Nostalos on 2008-10-23
Judging from what you posted and your config, I am not sure why you are trying to bridge.

If you are trying to bridge eth0 and eth1.  both your server and your router should be pulling a DHCP address from your service provider.  Most of which do not allow this.  I don't know the details there so I can't say.

But if you are wanting to truely bridge the two.   your configuration should look something like this.

> 
auto br0
iface br0 inet dhcp

auto eth0
iface eth0 inet manual
auto eth1
iface eth1 inet manual



However if you are just wanting your server to forward traffic to the internet for your router and everything behind it and NAT it on the way out, you do not want bridging but you want routing.

Remove the br0 configuration from your /etc/network/interfaces and uncomment the following line from your /etc/sysctl.conf file.

> #net.ipv4.ip_forward=1

then issue this command to make it active 
> sudo sysctl -p

this setting tells the kernel to forward on packets not destined for itself.

Next you need to NAT your private addressing to your public IP you receive from your ISP.

> iptables -t nat -A POSTROUTING -s 192.168.1.0/24 -o eth0 -j MASQUERADE

Note: this does NOT protect your server nor the systems behind it.

Now this being said I don't think this is an optimal setup, but it definatly can be done this way.   Personally if you are using Ubuntu to forward your traffic there is no need for a router.    Install DNSMasq and connect eth1 to a switch and drop the router all together.   

Or put the server behind the router and port forward the services you want to the server. i.e.  port 80 tcp for web traffic.

---

