---
title: "[SOLVED] Blocking DHCP for a single client"
date: 2008-03-30
forum: Networking &amp; Wireless
---

### Post by royolsen on 2008-03-30
I want to keep my Ubuntu 7.10 router/firewall from answering DHCP requests from a set-top-box. This box will get it's address information from a seperate bootp server. 

Unfortunately I can't find any way to do this directly in dhcpd3, except by specifying the mac address of every other host, and simply using the "deny unknown-hosts" statement on the scope decalaration. I'm still hoping to avoid this.

I figured it should be doable with iptables, unfortunately I can't get it to do what I want.

I've tried the following rules

```
iptables -I INPUT 1 -m mac --mac-source 00:02:9b:06:9f:39 -j DROP
iptables -I INPUT 1 -m mac --mac-source 00:02:9b:06:9f:39 -j LOG
```

resulting in 

```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination
LOG        0    --  anywhere             anywhere            MAC 00:02:9B:06:9F:39 LOG level warning
DROP       0    --  anywhere             anywhere            MAC 00:02:9B:06:9F:39
ACCEPT     0    --  anywhere             anywhere
```

Unfortunately, while the packet is being logged, it is first being picked up by dhcpd:

```
Mar 30 18:23:31 jade dhcpd: DHCPDISCOVER from 00:02:9b:06:9f:39 via br0
Mar 30 18:23:31 jade dhcpd: DHCPOFFER on 192.168.45.136 to 00:02:9b:06:9f:39 via br0
Mar 30 18:23:31 jade kernel: [3722369.703246] IN=br0 OUT= PHYSIN=eth1 PHYSOUT=tap0 MAC=ff:ff:ff:ff:ff:ff:00:02:9b:06:9f:39:08:00 SRC=0.0.0.0 DST=255.255.255.255 LEN=576 TOS=0x00 PREC=0x00 TTL=60 ID=0 PROTO=UDP SPT=68 DPT=67 LEN=556
```

Any help with preventing my dhcpd from responding to :9F:39 would be greatly appreciated!

---

### Post by Jose Catre-Vandis on 2008-03-30
Guess it is possible. With my netgear router I would appraoch in two ways; 1, block by MAC address, or 2. set a small range, and reserve all the IP addresses for computers I wanted to get their IP via dhcp

---

### Post by royolsen on 2008-03-30
Yes, I think there should definately be a way to do this. Hopefully someone can shed some light on why iptables is letting the filtered packages through to dhcpd.

---

### Post by Mr. C. on 2008-03-30
The DHCP server must receive RAW packets, before the INPUT chain, since DHCP requests are unaddressed broadcasts. See:

[http://lists.netfilter.org/pipermail/netfilter/2002-May/023826.html](http://lists.netfilter.org/pipermail/netfilter/2002-May/023826.html)


I believe in DHCPd 3, you can create a class that includes your single client, and then in the pool delcaration, use

deny members of "yourclass"

to deny DHCP access to that specific class.

---

### Post by royolsen on 2008-03-30
Thank you Mr.C, the information on raw packages was most helpfull.

As for the classes in dhcp3, I had already tried this without much success. As per your suggestion I decided to give it another shot, and while information on class configuration was very hard to find, I managed to get a working configuration:

```

*relevant configuration from dhcpd.conf*:

class "ignored" {
        match if substring(hardware,1,6) = 00:02:9b:06:9f:39;
}
subnet 192.168.45.0 netmask 255.255.255.0 {
        pool {
                deny members of "ignored";
                range 192.168.45.100 192.168.45.149;
        }
}

```

The dhcp server now happily ignores any requests from :9f:39 allowing the IPTV provider's server to work it's magic on the set top box.

Now I need to figure out why the IPTV (multicast probably) kills my Apple AirPort Express, but I suppose that is for another forum :)

---

### Post by Mr. C. on 2008-03-30
You're welcome.  Nice work!

---

