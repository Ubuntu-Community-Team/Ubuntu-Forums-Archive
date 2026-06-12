---
title: "Lost incoming/outgoing connection on port 80"
date: 2006-12-23
forum: Networking &amp; Wireless
---

### Post by cerrtkg on 2006-12-23
Greetings All,

**The Problem:** sites that I host cannot be accessed from outside the network, and I cannot surf to outside websites from within the server. I can access https (port 443) sites without problem, and I can access the ISPConfig control panel on port 81. Mail, FTP, etc. all work fine. _It seems that Port 80 isn't working on either incoming or outgoing connections._ Port 80 works just fine on other internal machines on the network which are also behind the router.

**Background:** I've been using Edgy Eft (using the "Perfect Setup) along with ISPConfig to host several sites successfully for months now, without any problems whatsoever. The server ran beautifully, in fact. Until yesterday. FWIW, there have been two recent changes to my system that I can think of. First, I changed my static IP address from 10.0.0.11 to 192.168.1.11, and I've installed the latest updates for the Ubuntu server. After making the IP address change, I've been able to access the hosted sites without problem, so I'm not sure what effect they've had on my predicament.

I have a cable connection and a Linksys router with port forwarding to my server. Here's the info from my /etc/network/interfaces:

[COLOR="Gray"]# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.1.11
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255
        gateway 192.168.1.1[/COLOR]

Every config file I've looked at at seems fine, and I have no internal firewall set up on the server. Even if I did, it wouldn't really account for the fact that I can't surf from Firefox, except for the encrypted sites (port 443)

Any pointers in the right direction would be greatly appreciated!

-Todd

---

### Post by choizy on 2006-12-23
My wild gues would be that the problem has something to do with you chaning the IP address. You say you have no firewall but I think you have some kind of iptables running :p

iptables -F
iptables -t nat -F
iptables -t mangle -F
iptables -X

Use this to clear your iptables and run your configuration again. Check that you changed the ip and net's everywhere in your configuration. Only thing I can think about is this.

---

### Post by cerrtkg on 2006-12-23
> **choizy said:**
> My wild gues would be that the problem has something to do with you chaning the IP address. You say you have no firewall but I think you have some kind of iptables running :p

iptables -F
iptables -t nat -F
iptables -t mangle -F
iptables -X

Use this to clear your iptables and run your configuration again. Check that you changed the ip and net's everywhere in your configuration. Only thing I can think about is this.

Thanks, choizy, for the suggestion. After all my troubleshooting woes, the problem ended up being related to the IP address switch, but was unrelated to Ubuntu or any type of server config issue. 

For anyone who finds this post and has a similar problem, it urns out that after I made the network change from 10.0.0 to 192.168.1, a Linksys router that was on my internal network designed to act as a switch (rather than a router) somehow must've reset itself to a previous setting, possibly during a windstorm we had within the last week. It started acting as a router again, giving itself an internal IP address for the old network and dishing out DHCP (creating two DHCP servers on the network). This must have confused the Ubuntu server for some reason on port 80, although all other TCP traffic remained unaffected. Once I changed the Linksys back to a switch/hub, all behaved normally again.


Todd

---

