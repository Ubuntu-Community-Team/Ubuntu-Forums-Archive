---
title: "About IPv6"
date: 2008-01-22
forum: Networking &amp; Wireless
---

### Post by berlowin on 2008-01-22
Guyz, I'm new in Linux and this my first time using Linux and i choose ubuntu for my project.

1. Anybody knows how to configure IPv6 in Linux?

2. How about the switch which device is connected several computer?
    does the switch must support IPv6 too?

3. Anybody knows about "teredo" and how it is used for network address translation?

Thanks for your information...

Regards,
Edwin

---

### Post by Steveway on 2008-01-22
1.Most Linux-distributions have IPV6 support allready enabled. 
You won't have to configure anything.
2. I'm not sure, are you talking about a private local network?
3. Never heard of it.

---

### Post by Dark Hornet on 2008-01-22
Yes, IPv6 is enabled by default on Ubuntu, with no configs needed.  With that said I am 95% sure you are NOT using IPv6, and instead using IPv4 which is the current standard and has been for decades.  Right now, IPv6 is used (at least in an ISP situation) for certain tunneling applications, and even then the IPv6 gets re-encapsulated into IPv4 in order to traverse the public network.  Personally I think that IPv6 is still a ways away from being standard due to the extreme cost in upgrading ALL equipment on the network level--with that said, you will probably hear MANY different opinions on when IPv6 will become standard.

---

### Post by BrentC on 2008-01-22
> **Dark Hornet said:**
> Yes, IPv6 is enabled by default on Ubuntu, with no configs needed.  With that said I am 95% sure you are NOT using IPv6, and instead using IPv4 which is the current standard and has been for decades.  Right now, IPv6 is used (at least in an ISP situation) for certain tunneling applications, and even then the IPv6 gets re-encapsulated into IPv4 in order to traverse the public network.  Personally I think that IPv6 is still a ways away from being standard due to the extreme cost in upgrading ALL equipment on the network level--with that said, you will probably hear MANY different opinions on when IPv6 will become standard.

Actually, there are a few ISPs in China and India using IPv6 because they can't hand out anymore IPv4 IP addresses.

---

### Post by Dark Hornet on 2008-01-22
> **BrentC said:**
> Actually, there are a few ISPs in China and India using IPv6 because they can't hand out anymore IPv4 IP addresses.

you are correct, infact, I think China is well on its way to being all IPv6...but in order for them to communicate with the rest of the world, at some point they need to re-encapsulate their packets in IPv4 headers.  The US on the other hand...depending on the ISP you are with usually has their backbone routers set up in a "parallel setup"...meaning they will have the standard Juniper M40, or T640, or Cisco 12410, or 12008, etc set up with IPv4, and then if needed--again, ONLY for specific apps at this time--they might have another device that handles only IPv6 traffic.  Well, this is at least how the ISP I work for handles things.

**note, this is a VERY basic description of how we run our IPv6***

---

### Post by netztier on 2008-01-22
> **berlowin said:**
> 
1. Anybody knows how to configure IPv6 in Linux?


If you didn't disable it (as some guides to troubleshooting Firefox suggest) it is already enabled and active.

Check the output of ifconfig -a :
```

ath0      Link encap:Ethernet  HWaddr 00:0F:20:94:AA:E4  
          inet addr:172.20.126.34  Bcast:172.20.126.255  Mask:255.255.255.0
          [COLOR="Red"]inet6 addr: fe80::20f:20ff:fe94:aae4/64[/COLOR] Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2394 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2316 errors:2 dropped:2 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1692115 (1.6 MB)  TX bytes:284085 (277.4 KB)

```

Very probably, you'll find an IPv6 address starting with fe:80, which is the default prefix for so-called *link-local* addresses. They're kind of similar to the RFC3330 IPv4 addresses from the 169.254.0.0/16 range: a host can give itself such an address if it does not conflict with another address from the local subnet - however routers should not forward packets for/from such addresses.

Other prefixes are available ("unique local IPv6 unicast addresses", RFC 4193), and they're somewhat similar in concept to the RFC1918 addresses we know as "private addresses" from IPv4 (such as 10.0.0.0, 172.[16-31].0.0 and 192.168.[0-255].0). There's tools online (like this [shell script]("http://www.hznet.de/tools/generate-rfc4193-addr")) that help you calculate an arbitrary and very possibly globally unique 48-bit prefix, starting with fc... or fd... Although it is very probable that such script-generated prefixes are globally unique (amongst other factors of randomness, they contain a representation of the NTP timestamp), they should not be visible nor routed on the Internet. However, they can make interconnecting networks a whole lot easier, for example when two large companies merge.

The network and host part of an IPv6 address are both 64bits long (and therefore, the concept of a "subnet mask" is to some extent obsolete), so with a 48bit prefix, you have 16bits of address space left to fill/use at your own gusto in the network part, for instance to create multiple subnets for your site (rather a lot, actually: 2^16 = 65536 subnets actually *is* quite a bit of a network)

Once you have calculated your prefix and chosen your subnet number, you can do the following in /etc/network/interfaces to set a static IPv6 address. Normally, you'd only do this on a router, but if you only need one subnet, any device on your subnet might do. 

```
iface eth0 inet6 static 
  address fd<calculated prefix><subnet number>:<host number>
  netmask 64

```

For your router to have the first address in the subnet, you can write (for <host number>) the shortcut :1 instead of 0000:0000:0000:0001. For <subnet number>, you can of course use all zeroes, so your IPv6 address will look like this:

```
iface eth0 inet6 static 
  address fd<calculatedprefix>::1
  netmask 64

```

Then, on that "router" (rather: prefix-advertiser), you should turn on the **radvd** (Router advertising deamon, available from the Ubuntu repositories) and configure it via /etc/radvd.conf

```
interface eth0 { 
  AdvSendAdvert on; 
  prefix fd<calculatedprefix><subnet number>/64
  { 
  }; 
};

```

Once radvd runs (may have to run /etc/init.d/networking restart), all IPv6-enabled devices on your subnet will have a second IPv6 address starting with fd:<something>. They form this address themselves, using the prefix advertised by radvd for the first 64bits of the address, and by transforming ther MAC address to EUI-64 notation, for using it as the host part of the address.

Now typing IPv6 addresses to ping each other is cumbersome - I suggest you also run a local **DNS server** that holds not only A records fo the IPv4 addresses, but also** AAAA records** for the IPv6 addresses of your hosts.

All of this will create only an IPv6 island in your network. Getting to talk to other IPv6 networks over the Internet is another story - of which I know even less.


> **berlowin said:**
> 
2. How about the switch which device is connected several computer?
    does the switch must support IPv6 too? 

No, they don't. An Ethernet frame containing an IPv6 packet instead of an IPv4 packet is still an Ethernet frame by all means and rights, and any Hub or Switch will happily transport it. Different however, if you want to log into the switch's web interface via IPv6 - their stripped-down IP stacks often have no IPv6 capabilities. Some alternative firmwares for some devices (such as the Linux-cabaple versions of Linksys' WRT-54G) may have IPv6 support, however.

best regards

Marc

---

### Post by berlowin on 2008-01-29
> **Steveway said:**
> 1.Most Linux-distributions have IPV6 support allready enabled. 
You won't have to configure anything.
2. I'm not sure, are you talking about a private local network?
3. Never heard of it.

answer no 2:
yes, may be, because i am blind about ipv6...

is there private network like IPv4 in ipv6?
ex : 192.168.0.1 or 10.0.0.0 :confused:

---

### Post by berlowin on 2008-01-29
> **Dark Hornet said:**
> Yes, IPv6 is enabled by default on Ubuntu, with no configs needed.  With that said I am 95% sure you are NOT using IPv6, and instead using IPv4 which is the current standard and has been for decades.  Right now, IPv6 is used (at least in an ISP situation) for certain tunneling applications, and even then the IPv6 gets re-encapsulated into IPv4 in order to traverse the public network.  Personally I think that IPv6 is still a ways away from being standard due to the extreme cost in upgrading ALL equipment on the network level--with that said, you will probably hear MANY different opinions on when IPv6 will become standard.

That's true, Pal... 
I want to apply ipv6 in my computer lab, but i don't know about the addressing ipv6 like the addressing in ipv4...
Ex: 1. Ipv4 have 5 classes, how about classes in ipv6?
      2. How about the private network (like 192.168.100.1 in ipv4) in ipv6?
      3. what is the ipv6 address if my computer has an ipv4 address 192.168.0.1? How to translate it?

thanks for your help so far...:)

---

### Post by berlowin on 2008-01-29
Oh my god **netztier**, I don't know how to thanks...
But i haven't tried your explanation, LOL...

Do you have YM or MSN?
I think I will ask you furthermore for another...
Because my English is not good...

Thx... :KS

---

