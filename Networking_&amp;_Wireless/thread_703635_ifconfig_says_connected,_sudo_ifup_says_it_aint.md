---
title: "ifconfig says connected, sudo ifup says it aint"
date: 2008-02-21
forum: Networking &amp; Wireless
---

### Post by rallion on 2008-02-21
Hey!

Some help will be appreciated, as i seem to be going round in circles!

Just installed Gutsy Gibbon and am connecting to our router via cable. The network icon in the top right corner is showing wired network with the black dot in and when i right click the icon and go "about connection" I get ip addresss and dns address. However i can't browse to a site ie facebook.com in firefox, yet if i use network tools and ping facebook.com i get replies.

So i've looked around the ubuntu documentation and tried some stuff from there.

If I open a terminal session and type "ifconifg". eth1 comes up showing an inet addr:, a bcast address and a mask. It also has UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1, not sure what else is important here.

however if i type "sudo ifdown eth1" it returns "interface eth1 not configured", yet when i'm in the network tools interface it shows eth1 with an ip address.

Hopefully, you can see from the above that i've tried a no of different options, but can't seem to get things working. Any help would be appreciated.

thanks in advance

---

### Post by spd106 on 2008-02-22
ifup and ifdown are just scripts that call ifconfig (or rather it's replacement ip), so trust ifconfig first and foremost.

If you can ping successfully then you are connected ok, it's sound more like an application specific problem. The most common issue it relate to IPv6 and there are numerous threads discussing this on the forum. So it might be worth having a look at a few of them. I think there also a page in the help wiki on this.

Other than that you could try installing another web browser if Synaptic works. Probably start with Epiphany and then maybe Opera or Konqueror.

---

### Post by whit on 2008-03-02
> **spd106 said:**
> ifup and ifdown are just scripts that call ifconfig (or rather it's replacement ip), so trust ifconfig first and foremost.

Looks to be a bug involved. Usually ifup and ifdown work fine on Ubuntu 7.10. But now I'm looking at a system where (logged in as root);

```

# ifdown eth1
ifdown: interface eth1 not configured

```

yet

```

# ifconfig eth1
eth1      Link encap:Ethernet  HWaddr 00:1B:B9:6B:A0:CF  
          inet addr:xxx.yyy.237.70  Bcast:xxx.yyy.236.79  Mask:255.255.255.240
          inet6 addr: fe80::21b:b9ff:fe6b:a0cf/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:236 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:14160 (13.8 KB)  TX bytes:468 (468.0 b)
          Interrupt:19 Base address:0xec00 

```

and in /etc/network/interfaces

```

auto eth1
iface eth1 inet static
address xxx.yyy.237.70
netmask 255.255.255.240

```
(note "xxx.yyy" replaces the real numbers)

Now, I've got another Ubuntu 7.10 sytem that has just that much configuration, and on which ifup and ifdown work just fine specifying the interface. (Also, ifup and ifdown are not scripts, they're compiled code.) Does someone know what the bug is that causes them to fail on some but not most Ubuntu 7.10 systems? I do, for my purposes, actually need them to work.

---

