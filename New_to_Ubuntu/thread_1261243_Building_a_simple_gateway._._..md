---
title: "Building a simple gateway. . ."
date: 2009-09-08
forum: New to Ubuntu
---

### Post by pi.boy.travis on 2009-09-08
Hi!  I am trying to setup an old computer as a gateway.  I have my two network cards, ufw for firewall, DHCP, DNS caching, Squid for proxy, and all that stuff.  I just can't figure out how to get internet traffic to flow from eth0 through eth1 to my clients.  How do I go about doing this?  Do I have to bridge them somehow?  Do I need some application to do it?  Any advice on how to go about this would be greatly appreciated.

Thanks in advance!

---

### Post by ainsworth_t on 2009-09-08
I came across a really good tutorial a while back if you feel like starting from scratch. It covers building a firewall/gateway with Debian, but it still applies to Ubuntu. It's also a bit outdated, so you'll probably have to read some man pages for some of the applications. I'm working on getting an updated tutorial over the same topic together.

[http://www.cyberdogtech.com/firewalls/](http://www.cyberdogtech.com/firewalls/)

---

### Post by pi.boy.travis on 2009-09-08
OK, now I see that the component I am missing is NAT and IPmasquerading.  Looks like I am going to learn how to use iptables. . .

---

### Post by bodhi.zazen on 2009-09-08
> **pi.boy.travis said:**
> Hi!  I am trying to setup an old computer as a gateway.  I have my two network cards, ufw for firewall, DHCP, DNS caching, Squid for proxy, and all that stuff.  I just can't figure out how to get internet traffic to flow from eth0 through eth1 to my clients.  How do I go about doing this?  Do I have to bridge them somehow?  Do I need some application to do it?  Any advice on how to go about this would be greatly appreciated.

Thanks in advance!

In general you want to put as few applications as possible on your "firewall".

You will need to either configure iptables manually or you can use shorewall or guarddog.

When configuring iptables you need to either NAT or masquerade.

[http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch14_:_Linux_Firewalls_Using_iptables#Allowing_Your_Firewall_To_Access_The_Internet](http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch14_:_Linux_Firewalls_Using_iptables#Allowing_Your_Firewall_To_Access_The_Internet)

I advise you consider using a firewall specific distro such as ipcop.

---

### Post by pi.boy.travis on 2009-09-08
> **bodhi.zazen said:**
> In general you want to put as few applications as possible on your "firewall".

You will need to either configure iptables manually or you can use shorewall or guarddog.

When configuring iptables you need to either NAT or masquerade.

[http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch14_:_Linux_Firewalls_Using_iptables#Allowing_Your_Firewall_To_Access_The_Internet](http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch14_:_Linux_Firewalls_Using_iptables#Allowing_Your_Firewall_To_Access_The_Internet)

I advise you consider using a firewall specific distro such as ipcop.

Thanks for the excellent link!   I think this may do the trick.

---

### Post by pi.boy.travis on 2009-09-08
It works!

sysctl to enable ip4 packet forwarding

enable forwarding in nat table and turn on masquerading!

---

### Post by bodhi.zazen on 2009-09-08
Always nice to see people learn iptables =)

masquerading is nifty :lolflag:

---

### Post by pi.boy.travis on 2009-09-09
> **bodhi.zazen said:**
> Always nice to see people learn iptables =)

masquerading is nifty :lolflag:

Yeah, it wasn't as difficult as I expected.  The toughest part was figuring out how to make the rules permanent.

---

