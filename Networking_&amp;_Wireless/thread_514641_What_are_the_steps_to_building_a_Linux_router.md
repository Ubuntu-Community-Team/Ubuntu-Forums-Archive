---
title: "What are the steps to building a Linux router"
date: 2007-08-01
forum: Networking &amp; Wireless
---

### Post by tuprox on 2007-08-01
I have seen a number of posts about people asking how to setup a Linux router with Ubuntu.  There are some tutorials, but the all leave much to be desired.  I have tried 3 different ones and they all fail.  What is strange is that I found a large number of tutorials for building a Fedora router, but few and low quality guides for Ubuntu.  Please don't make me go to Fedora to get this working!!:(

If someone helps I promise to write a beautiful tutorial for the world to use.  I'm just looking at a basic setup now.  1 PC, 2 NIC's and no wireless until the router is up and running.

I noticed there is a web interface that allows me to control the settings of IPTables.  [www.webmin.com]("http://www.webmin.com") 

Pleae help an avid Linux user keep using the Ubuntu distro!

---

### Post by splintercellguy on 2007-08-01
IPcop is apparently good, but not Ubuntu tho.

---

### Post by tuprox on 2007-08-01
Could you please explain in a little more detail.  That is rather vague.  Can IPCop run on Ubuntu? What is it?

---

### Post by digilink on 2007-08-01
>  		Could you please explain in a little more detail.  That is rather vague.  Can IPCop run on Ubuntu? What is it?

IPCop is a standalone firewall distribution that is meant to do just that, nothing else. 

I have kicked around this idea myself many times over. I had a Debian based firewall up and running and it did what I needed it to do, but when it boils down to it, it's just not as robust as a pre-built solution unless you are willing to invest some serious time into it. 

I use Smoothwall, it's linux based, and there is a very active community and many mods that have been written for it. Smoothwall is currently under active development and version 3 which is now in Beta looks extremely promising. 

Check it out here: [http://www.smoothwall.org](http://www.smoothwall.org)

And if you still want to roll your own, there is a decent Debian based tutorial here:
[http://www.cyberdogtech.com/firewalls/](http://www.cyberdogtech.com/firewalls/)

Also worth mentioning is a book that I am keeping an eye on, it is due out to be published sometime this fall, looks real interesting:
[http://nostarch.com/firewalls.htm](http://nostarch.com/firewalls.htm)

Hope that helps.

---

### Post by roaldz on 2007-08-01
Have you been introduced to IPtables?

There is a very good guide for Gentoo linux [http://www.gentoo.org/doc/en/home-router-howto.xml]("here")
be carefull, don't just copy&paste this one, its for gentoo, a WHOLE other distro than Ubuntu. The IPtables rules are good though:

```
First we flush our current rules
# iptables -F
# iptables -t nat -F

Setup default policies to handle unmatched traffic
# iptables -P INPUT ACCEPT
# iptables -P OUTPUT ACCEPT
# iptables -P FORWARD DROP

Copy and paste these examples ...
# export LAN=eth0
# export WAN=eth1

Then we lock our services so they only work from the LAN
# iptables -I INPUT 1 -i ${LAN} -j ACCEPT
# iptables -I INPUT 1 -i lo -j ACCEPT
# iptables -A INPUT -p UDP --dport bootps -i ! ${LAN} -j REJECT
# iptables -A INPUT -p UDP --dport domain -i ! ${LAN} -j REJECT

(Optional) Allow access to our ssh server from the WAN
# iptables -A INPUT -p TCP --dport ssh -i ${WAN} -j ACCEPT

Drop TCP / UDP packets to privileged ports
# iptables -A INPUT -p TCP -i ! ${LAN} -d 0/0 --dport 0:1023 -j DROP
# iptables -A INPUT -p UDP -i ! ${LAN} -d 0/0 --dport 0:1023 -j DROP

Finally we add the rules for NAT
# iptables -I FORWARD -i ${LAN} -d 192.168.0.0/255.255.0.0 -j DROP
# iptables -A FORWARD -i ${LAN} -s 192.168.0.0/255.255.0.0 -j ACCEPT
# iptables -A FORWARD -i ${WAN} -d 192.168.0.0/255.255.0.0 -j ACCEPT
# iptables -t nat -A POSTROUTING -o ${WAN} -j MASQUERADE
Tell the kernel that ip forwarding is OK
# echo 1 > /proc/sys/net/ipv4/ip_forward
# for f in /proc/sys/net/ipv4/conf/*/rp_filter ; do echo 1 > $f ; done
```But watch the 192.168.0.0's there

Roald

---

### Post by Junglizer on 2007-08-01
From the hardware layout I would recommend no less then 3 NICs and if you're throwing wireless into the mix possilby 4.  
NIC 0 (RED) - IN
NIC 1 (GREEN) - OUT
NIC 2 (Yellow) - DMZ
NIC 3 (Yellow) - Wireless, probably best to be DMZ also.

Also pf (packetfilter) is, according to most people, better then IPtables. This comes on [OpenBSD]("http://www.openbsd.org"). Another firewall distro is [SmoothWall]("http://www.smoothwall.org/").

---

### Post by roaldz on 2007-08-03
> **Junglizer said:**
> From the hardware layout I would recommend no less then 3 NICs and if you're throwing wireless into the mix possilby 4.  
NIC 0 (RED) - IN
NIC 1 (GREEN) - OUT
NIC 2 (Yellow) - DMZ
NIC 3 (Yellow) - Wireless, probably best to be DMZ also.

Also pf (packetfilter) is, according to most people, better then IPtables. This comes on [OpenBSD]("http://www.openbsd.org"). Another firewall distro is [SmoothWall]("http://www.smoothwall.org/").
BSD's have always been better with firewalling, PF is just a better system:)
When you have to set up a GOOD firewall FAST, I'd go with [PFsense]("http://www.pfsense.com/"). PFsense is a 26Meg BSD based firewall livecd. It's complete with everything you might ever need on a firewall. Configuration is very simple, its just a web interface:)

Roald

---

