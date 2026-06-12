---
title: "network gateway problem"
date: 2008-07-18
forum: Networking &amp; Wireless
---

### Post by pawebst on 2008-07-18
Hi guys,
I'm new at posting and relatively new at ubuntu but have been involved with unix and windows professionly. I have just inherited a computer with ubuntu 8.04/xp on it which I have connected to my small home network. The network is connected via a switch to my modem which is also my DCHP server with ip address range of 192.168.2.4-6 with it's own ip address of 10.1.1.1. All of my XP machines automatically have their ip address and gateway setup ie 192.168.2.4 gateway 10.1.1.1 and can connect to the internet. This also happens to the xp partition of the new box, but when I use the ubuntu partition the internet is unreachable. Netstat -rn shows:
Destination  Gateway Genmask       flags Mss Window irtt  Iface
192.168.2.0  0.0.0.0 255.255.255.0 U      0  0       0    eth0
169.254.0.0  0.0.0.0 255.255.0.0   U      0  0       0    eth0

I have tried to set the gateway in network manager but it still doesn't stick and I have tried to manually add the gateway as such:
sudo route add default gw 10.1.1.1 - which returns:
SDIOCADDRT: No such process

I can't seem to add the gateway to the machine. It can ping the 192.168.2.X subnet machines no problems but can't ping 10.1.1.1.

Any suggestions?

P.S I have uninstalled the gnome network manager via synaptic as was suggested on a post elsewhere but still can't manually configure the network.

Any help is much appreciated.

---

### Post by David Robertson on 2008-07-18
Hope the following helps.

Your gateway is on a different subnet 10ish to your Linux box 192ish. So Linux has no idea how to get to the gateway.

You can either:

1. Tell linux to use it adaptor as the gateway - specify eth0 etc instead of 10.0.0.1. Linux will then just broadcast like your XP machines and the gateway will pick them up.

2. Change your router DHCP or it's IP address. Make the router 192.168.1.100 - anything outside the DHCP range or change the range to 10.0.0.2 to 10.0.0.50 (with the router still at 10.0.0.1.

You'll have to get the desktops to pickup the new addresses. Either reboot or turn off the router or disconnect the computers network cable or:
For XP: ipconfig /renew
For Linux: sudo /etc/init.d/networking restart

NB: if you change your router's ip address through a browser, it will disappear until you browse to the new address.

---

### Post by pawebst on 2008-07-18
Thanks David,

Can you expand on using the adaptor as a gateway. Is this similar to RIP and continually broadcasts discovery packets? I'm just not quite sure how to set that up. I realise the other option was available but figured I'd be able to tell the machine the gateway address and that would let packets out of the subnet but it doesn't like that, any reason you know of why this is so?

Anyway thanks again.

---

### Post by pawebst on 2008-07-20
This is for anyone who wants closure on this thread - 

The solution as suggested by David in detail is the following:

sudo route add -host 10.1.1.1 eth0  - gateway ip outside subnet

sudo route add default gw 10.1.1.1 eth0

This will allow packets to crossover from one subnet to the other via a single interface and allow internet access.

---

### Post by Scharpe on 2008-07-22
That might make it work, but a Guillotine cures a headache too.

The gateway and the computer connecting to it should be on the same subnet, as David said - that's just how networking is done.  Forcing the computer to talk to a gateway it really shouldn't be talking to isn't how this stuff was designed to work.  It works, but it's not very efficient.

You should see some improvement if you either give the Linux box a 10.1.1.x address, or move the router to the 192.168.1 subnet.  Either one is correct - forcing cross-subnetting isn't.

---

