---
title: "VirtualBox guest and host not communicating."
date: 2009-02-20
forum: New to Ubuntu
---

### Post by rgb96 on 2009-02-20
Hey guys and gals,

I am running Ubuntu 8.10 and a virtual machine with Windows XP that I made with VirtualBox. I gave my virtual machine internet by creating a bridge and tapline on my host and passing tap0 to the guest with the host interface option, so I could give the machine a static IP. This works fine for the most part. I can reach the internet from the guest and can ping everything on my network, except for the host machine. The host can't ping the guest either. This communication is rather important, since my ultimate  goal is to create an SSH connection between them. Maybe I missed a step somewhere? 



```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet manual

auto tap0
	iface tap0 inet manual
	tunctl_user me
	uml_proxy_arp 10.x.xx.xxx
	uml_proxy_ether eth0

auto br0
	iface br0 inet static
	address 10.x.xx.xxx
	netmask 255.255.255.0
	gateway 10.x.xx.254
	bridge_ports eth0 tap0
	bridge_maxwait 0
```

Any help would be much appreciated.

---

### Post by superprash2003 on 2009-02-20
have you tried pinging by ip or hostname?

---

### Post by rgb96 on 2009-02-20
Yeah. I couldn't ping either way, but I've fixed it now. I had to change the default gateway of the bridge to be the IP of the virtual machine. Thanks for the reply though.

---

### Post by tarps87 on 2009-02-20
In the guest machines settings are you using NAT or host interface networking?
Ping will not work with NAT, where as in host interface mode ping and ssh should work

Edit:
Just seen you have fixed it

---

