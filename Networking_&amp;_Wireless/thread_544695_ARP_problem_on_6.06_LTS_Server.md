---
title: "ARP problem on 6.06 LTS Server"
date: 2007-09-06
forum: Networking &amp; Wireless
---

### Post by grimbanjo7 on 2007-09-06
Basically, I have a server that can't see any ARP requests other than ones that it sends out. It's running 6.06 server (64-bit) with 2 built-in Intel e1000 NICs although only one of them is being used. The one being used is setup for a static IP with the following config:
```

auto eth0
iface eth0 inet static
        address 10.128.48.55
        netmask 255.255.254.0
        network 10.128.48.0
        broadcast 10.128.48.255
        gateway 10.128.48.5

```
I can reach it from my desktop and use SSH, etc. if I add its MAC address manually but that isn't really a solution. I found out that it can't see any ARP requests using tcpdump but it can send/receive ARP to other machines just fine. Our network is mostly using DHCP but I have another server with a static address that has no problems. Also, when using a livecd, everything works fine. 

I've looked at sysctl for ARP filtering but everything is at its default. I've tried changing the kernel but that didn't help either. I've run out of things to try and looked on google and these forums but I can't seem to find anything. Any help would be appreciated.

---

### Post by noob12 on 2007-09-06
Your config looks wrong to me; either the netmask or broadcast.

Do you really mean to have that 23 bit mask?  That's unusual; however, if you really meant that, your broadcast address would normally be 10.128.49.255 for that host address.

If you meant to have the 24 bit mask, the netmask should be 255.255.255.0 (and then the broadcast is ok).

Change one or the other and I expect ARP and other broadcast traffic will start working.

---

### Post by grimbanjo7 on 2007-09-07
Our local network has 2 subnets, 10.128.48.0 and 10.128.49.0 all on one set of switches. I've tried a netmask of 255.255.255.0 but that only cuts me off from the server completely. A broadcast of 10.128.49.255 doesn't do anything. I checked on another server on the 48 subnet we have which works (windows based) and it has the same configuration except for the ip. 

The server can send ARP requests and get replies but it just can't see any requests made by other machines. Here's an example:
```

tcpdump -en arp
tcpdump: verbose output suppressed, use -v or -vv for full protocol decode
listening on eth0, link-type EN10MB (Ethernet), capture size 96 bytes
08:48:20.489967 00:13:72:63:8d:77 > 00:e0:29:32:f4:32, ethertype ARP (0x0806), length 64: arp reply 10.128.48.17 is-at 00:13:72:63:8d:78
08:48:20.490073 00:13:72:63:8d:77 > 00:e0:4c:7a:9e:09, ethertype ARP (0x0806), length 64: arp reply 10.128.48.17 is-at 00:13:72:63:8d:78
08:52:26.858628 00:13:72:63:8d:77 > 00:04:5a:40:7c:33, ethertype ARP (0x0806), length 64: arp reply 10.128.48.17 is-at 00:13:72:63:8d:78
08:52:26.858753 00:13:72:63:8d:77 > 00:90:27:17:4a:dc, ethertype ARP (0x0806), length 64: arp reply 10.128.48.17 is-at 00:13:72:63:8d:78
08:53:22.919745 00:13:72:63:8d:77 > 00:04:5a:40:7c:33, ethertype ARP (0x0806), length 64: arp reply 10.128.48.17 is-at 00:13:72:63:8d:78
08:53:22.919746 00:13:72:63:8d:77 > 00:90:27:17:4a:dc, ethertype ARP (0x0806), length 64: arp reply 10.128.48.17 is-at 00:13:72:63:8d:78
08:57:41.184951 00:20:ed:76:45:e9 > 00:0d:9d:4b:b2:59, ethertype ARP (0x0806), length 60: arp reply 10.128.48.29 is-at 00:20:ed:76:45:e9

7 packets captured
14 packets received by filter
0 packets dropped by kernel

```

During this time period there should have been many ARP requests/replies (as in any normal network) but it only sees a few replies. The server can arping anything else but not the other way around.
```

server
ARPING 10.128.49.36 from 10.128.48.55 eth0
Unicast reply from 10.128.49.36 [00:13:72:E4:43:15]  4.080ms
Unicast reply from 10.128.49.36 [00:13:72:E4:43:15]  0.727ms
Unicast reply from 10.128.49.36 [00:13:72:E4:43:15]  0.762ms
Unicast reply from 10.128.49.36 [00:13:72:E4:43:15]  0.674ms
Sent 4 probes (1 broadcast(s))
Received 4 response(s)

desktop
ARPING 10.128.48.55 from 10.128.49.36 eth0
Sent 4 probes (4 broadcast(s))
Received 0 response(s)

```

---

### Post by noob12 on 2007-09-07
> 
During this time period there should have been many ARP requests/replies (as in any normal network) but it only sees a few replies. The server can arping anything else but not the other way around.

Note that in a given period you'll see ARPs only from other hosts whose cache entry for 10.128.48.55 has already expired from their arp caches.  Otherwise they will normally use their cache and not send an ARP request.

Also note that with arping, the response is being sent unicast (i.e. direct to the source ip), so this avoids the broadcast issue on reception of replies to an arping.

I'm really not sure what the behavior will be if the netmask and broadcast don't logically match.   The expected broadcast for you situation would be 10.128.49.255 (set on *all* your hosts).   The problem may be compounded if the other hosts also have the wrong broadcast set.  You may want to consult an alternate source you trust to confirm.  There are also subnet/broadcast calculators out on the web.

---

### Post by grimbanjo7 on 2007-09-10
I've solved the problem by compiling the latest driver source from intel which brings the version from 7.0.33 (I think) to 7.6.5. Even though the problem was ultimately just driver related, thanks for your help noob12.

---

### Post by noob12 on 2007-09-10
Thanks for providing that instruction.

---

