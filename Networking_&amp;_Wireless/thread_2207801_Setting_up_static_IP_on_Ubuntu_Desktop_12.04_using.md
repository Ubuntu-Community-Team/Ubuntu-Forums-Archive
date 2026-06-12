---
title: "Setting up static IP on Ubuntu Desktop 12.04 using VMWare Workstation"
date: 2014-02-25
forum: Networking &amp; Wireless
---

### Post by zodac on 2014-02-25
I'm looking for some help in setting up a static IP on my VM, while still having access to the internet. I'd like to be able to pull/push things from Github, while also putting a Tomcat server on the network.

At the moment, I have two /etc/network/interfaces setups:

1) **Network Adaptor: NAT**
auto eth0
iface eth0 inet dhcp

This gives me access to the internet, but can't put Tomcat on the network.

2) [B]Network Adaptor: Bridged
[/B]auto eht0
iface eth0 inet static

address 147.252.91.223
network 147.252.91.0
netmask 255.255.255.0
gateway 147.252.91.1

This puts the Tomcat webapp out on 147.252.91.223:8080, but I can't connect to the internet itself.

I've tried tutorials online, but I can only ever get one or the other working - never both.

---

### Post by TheFu on 2014-02-25
Don't know anything about VMware Workstation (btw, thanks for saying the full name!), but I do know that of the 5 other VM tools that I've used, whether a static IP is used or not is completely up to the clientOS.  The hostOS only controls whether the network is a full-LAN OS (bridged) or shoved into a compartment only to beg for input packets from the hostOS - NAT.

So - use bridged networks from the host and setup static IPs inside any ClientOSes as you normally would.

There are typos in your "bridged" example. Are those really there or just in the post here?
It would help me if you could be very clear about which settings are on the hostOS and inside the clientOS. The networking IP/mask/gw for each side would be helpful too.   The overall network where this stuff sits  would be good to know too - is this at home, at work, at a VPS?  Those networks are usually extremely different.

Oh ... and where do you want the java webapp available?  Internally or on the public internet?

---

### Post by zodac on 2014-02-25
Well, I took that direct from my network/interfaces file - if there are any typos, they're not giving me any errors.

I'm not sure what information you're looking for, so bear with me. Here's the ifconfig/ipconfig from the VM and the host:

[IMG]http://i.imgur.com/Q52zjQs.png[/IMG]

[IMG]http://i.imgur.com/HVAgQNp.png[/IMG]


And here's the network settings from the VM:

[IMG]http://i.imgur.com/Mx5yAld.png[/IMG]


This is being run on college computers. I don't know if it makes a difference, but we have individual computers - no-one else will be using this machine but me.

I'd like the app to be available on the public internet. I **can** do that at the moment, but I lose the ability to connect to the internet on the VM when doing that (which is odd - I can put something on the internet, but can't connect to it).

---

### Post by chili555 on 2014-02-25
> auto [COLOR="#FF0000"]eth[/COLOR]0
iface eth0 inet static

address 147.252.91.223
network 147.252.91.0
netmask 255.255.255.0
gateway 147.252.91.1Typically, when you set up a static IP, you are also responsible for DNS nameservers. Although I have little experience with VMware, I'd try:```
auto [COLOR="#FF0000"]eth[/COLOR]0
iface eth0 inet static

address 147.252.91.223
network 147.252.91.0
netmask 255.255.255.0
gateway 147.252.91.1
dns-nameservers 8.8.8.8 147.252.91.1
```

---

### Post by zodac on 2014-02-25
> **chili555 said:**
> Typically, when you set up a static IP, you are also responsible for DNS nameservers. Although I have little experience with VMware, I'd try:```
auto [COLOR=#FF0000]eth[/COLOR]0
iface eth0 inet static

address 147.252.91.223
network 147.252.91.0
netmask 255.255.255.0
gateway 147.252.91.1
dns-nameservers 8.8.8.8 147.252.91.1
```

That worked perfectly. Thank you very much - this'll save me a hell of a lot of time over the next few weeks. Ridiculous how much difference one line can make.

Thank you again, and to you [COLOR=#000000]TheFu. [/COLOR]:P

---

### Post by TheFu on 2014-02-25
UNIX systems do what you ask, even if it is not what you intend. We all have made similar mistakes ... er ... this week. ;)
Anyway, please mark the thread as SOLVED.

---

