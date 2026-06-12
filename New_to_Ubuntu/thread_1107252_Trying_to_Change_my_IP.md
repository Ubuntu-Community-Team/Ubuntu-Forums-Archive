---
title: "Trying to Change my IP"
date: 2009-03-26
forum: New to Ubuntu
---

### Post by alanfang on 2009-03-26
I am trying to change my IP computers from the command line as described in this tutorial,

[http://www.cyberciti.biz/faq/ubuntu-linux-change-ip-address/](http://www.cyberciti.biz/faq/ubuntu-linux-change-ip-address/)

here is what it says to do,

```
sudo gedit /etc/network/interfaces

Find eth0 section and setup IP address as follows:

auto eth0
iface eth0 inet static
address 192.168.2.1
netmask 255.255.255.0
network 192.168.2.0
broadcast 192.168.2.255
Save and close the file. Once done, restart network:
$ sudo /etc/init.d/networking restart

Verify new IP address:
$ ifconfig eth0
$ ifconfig
```


The difference is I want to change it for my wireless card, not my ethernet so I am just replacing eth0 with ra0. I edited it as described in the tutorial, and it does change the IP according to ifconfig. The problem is it also prevents me from connecting to the internet. Do I have to format the IP in some special way to do this? Thanks for the help.

---

### Post by kpatz on 2009-03-26
How are you connected to the Internet?  What ISP are you using?  Are you using a router?

If you're not using a router (PC connected directly to a modem), you'll have to use either DHCP or PPPOE depending on your ISP, unless they give out static IP addresses.  If you are using a router, you'll have to either use DHCP (router provides the IP), or assign a static IP on the same subnet as what the router is using.

What IP do you get from the router via DHCP and what IP are you trying to assign statically?

For example, say you get an IP from your router 192.168.1.10 and the subnet mask is 255.255.255.0.  If you want a static IP you'll have to use one in the range 192.168.1.1 thru 192.168.1.254, excluding addresses already in use.  Also, make sure to set the subnet mask, broadcast and gateway addresses correctly.  If you don't (especially the gateway) you won't be able to talk to anything outside your LAN.

---

### Post by alanfang on 2009-03-26
I am connecting to a router. I do not know whether it is static or DHCP. My original IP was of the pattern xx.x.x.xxx. How do I determine my broadcast and gateway addresses? Thank you for the help.

---

### Post by davecgs on 2009-03-26
Wow this is a can of worms. 

All internet routers are DHCP.  I find it impossible to believe that an internet router supports a static IP address. 

Now, first I would STRONGLY suggest a hardware firewall such as from Linksys or Dlink.  Connecting conputer to router is common but it's a major security risk.  That's what I have and I feel much safer AND that allows a static IP address. 

Now, on my hardware router, I have it setup to accept DHCP from my ISP.  It then generates  non-routable IP addresses for the rest of the computers.  The firewall of course allows me to hit the internet through a gateway (more about that in a second)

Anyway, in my case that IP address list is 192.168.10.100 - 192.168.10.160 which is of course overkill since I don't have 60 computers however I could easily setup static address on each machine and just use a gateway to point to the router. 

Now what is a gateway.

When I setup a non routable address on a machine (192.168.10.x or 10.10.10.x) etc these won't see the internet.  I then define a special IP address called a gateway which says "if you ping [www.novell.com](www.novell.com) and I don't know how to handle that, then I'll pass it to the firewall (in my case) and the firewall will pass it to the cable router and it will say "hey no problem...Novell here we come and then pass that information back to the computer.  

Now the question is where to setup a gateway address.  Many people use the route add command but I've never had much success with it.  I use the actual configuration files.  IN Fedora it's /etc/sysconfig/network and you type GATEWAY=192.168.10.1 or whatever it is.  For Ubuntu just add the line gateway=192.168.10.1 or whatever it is to the ifconfig file /etc/network/interfaces.  Next you'll have a problem with names so you need to tell it the name server.  The name server is added in /etc/resolve and again add the same IP address
nameserver 192.168.10.1

Don't you wish you stuck with DHCP!

Dave...

---

### Post by MJWitter on 2009-03-26
Just something to try, some routers have a web set-up page(usually the ip address of the router) where one can change the settings and a few are able to set specific pc's to static IPs using their mac address.  Those without set IPs are still assigned using DHCP.

---

### Post by kpatz on 2009-03-26
> **alanfang said:**
> I am connecting to a router. I do not know whether it is static or DHCP. My original IP was of the pattern xx.x.x.xxx. How do I determine my broadcast and gateway addresses? Thank you for the help.Was your original IP 10.x.x.xxx?  That's a private IP range, given out by your router ( as is 192.168.x.x) and is safe to post here.

Do an **ifconfig -a** while you're connected the normal way (DHCP) and you should see your IP address, netmask and broadcast addresses.  Here's the ones of one of my boxes (see the bolded line):

> kpatz@mythtv:/etc$ ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:18:f3:75:ef:75
          **inet addr:192.168.0.109  Bcast:192.168.0.255  Mask:255.255.255.0**
          inet6 addr: fe80::218:f3ff:fe75:ef75/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:191387 errors:0 dropped:0 overruns:0 frame:0
          TX packets:183371 errors:0 dropped:0 overruns:0 carrier:2
          collisions:0 txqueuelen:1000
          RX bytes:178032143 (169.7 MB)  TX bytes:72745507 (69.3 MB)

To get your gateway, enter the command **netstat -rn.**

> kpatz@mythtv:/etc$ netstat -rn
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.0.0     0.0.0.0         255.255.255.0   U         0 0          0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 eth0
0.0.0.0         **192.168.0.1**     0.0.0.0         UG        0 0          0 eth0
The last line (starting with 0.0.0.0) has the gateway IP.

So, for this example, since my IP starts with 192.168.0.x, my netmask is 255.255.255.0, broadcast is 192.168.0.255 and gateway of 192.168.0.1, if I wanted to use a static IP (which would have to be in the 192.168.0.x netblock), I would do this in /etc/network/interfaces (here I'm using 192.168.0.10):

```

iface eth0 inet static
        address 192.168.0.10
        netmask 255.255.255.0
        network 192.168.0.0
        broadcast 192.168.0.255
        gateway 192.168.0.1
        # dns-* options are implemented by the resolvconf package, if installed
        dns-nameservers 192.168.0.1
        dns-search my-domain.com

```

To get the dns-nameservers and dns-search, look in /etc/resolv.conf.

---

### Post by alanfang on 2009-03-26
> **kpatz said:**
> Was your original IP 10.x.x.xxx?  That's a private IP range, given out by your router ( as is 192.168.x.x) and is safe to post here.

Do an **ifconfig -a** while you're connected the normal way (DHCP) and you should see your IP address, netmask and broadcast addresses.  Here's the ones of one of my boxes (see the bolded line):



To get your gateway, enter the command **netstat -rn.**


The last line (starting with 0.0.0.0) has the gateway IP.

So, for this example, since my IP starts with 192.168.0.x, my netmask is 255.255.255.0, broadcast is 192.168.0.255 and gateway of 192.168.0.1, if I wanted to use a static IP (which would have to be in the 192.168.0.x netblock), I would do this in /etc/network/interfaces (here I'm using 192.168.0.10):

```

iface eth0 inet static
        address 192.168.0.10
        netmask 255.255.255.0
        network 192.168.0.0
        broadcast 192.168.0.255
        gateway 192.168.0.1
        # dns-* options are implemented by the resolvconf package, if installed
        dns-nameservers 192.168.0.1
        dns-search my-domain.com

```

To get the dns-nameservers and dns-search, look in /etc/resolv.conf.

Ah, so that is a private address, makes much more sense. Thanks for the gateway and netmask descriptions as well. I managed to get my IP changed and things appear to be working at this point.

---

