---
title: "Mysterious UDP packets on port 137 (netbios-ns)"
date: 2017-03-01
forum: Networking &amp; Wireless
---

### Post by bquade on 2017-03-01
I am running Ubuntu 16.04 on a computer that is connected to a wireless router which is also my local network's gateway. Recently I noticed that my computer was sending repeated UDP packets to port 137 on my router. This happens about every fifteen minutes or so, and it sends several messages before trying again. The router ignores these packets because port 137 is not open, so WireShark 2.0.2 reports "Destination unreachable" for those packets. I can ping the router just fine. Port 137 is for NETBIOS and I don't use it, and as far as I know it is mostly a Windows thing. I don't run Windows at all. It could be harmless, but it could be a problem too. So I would like to know what application it is.

This is the UDP message I get from WireShark
```
 User Datagram Protocol, Src Port: 24787 (24787), Dst Port: netbios-ns (137)
```

And here is what netstat showed me
```
# netstat -apu
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
udp        0      0 *:mdns                  *:*                                 13145/avahi-daemon:
udp        0      0 *:54731                 *:*                                 13145/avahi-daemon:
udp        0      0 hostname:domain          *:*                                 1407/dnsmasq    
udp        0      0 *:bootpc                *:*                                 26589/dhclient  
udp6       0      0 [::]:42193              [::]:*                              13145/avahi-daemon:
udp6       0      0 [::]:mdns               [::]:*                              13145/avahi-daemon:

```

I tried shutting down my browsers and email clients, but the packets still kept sending. I tried killing cups, samba and avahi-daemon but the packets still kept sending. I don't know how to kill dnsmasq and dhclient, and I'm not sure what the consequences might be if I did, so I've been reluctant to kill anything else on my system. Does anyone know if dnsmasq or dhclient sends packets to port 137, or know if it is okay to kill those processes?

Is it normal for Linux applications to look for hosts that have port 137 open? What other applications that run on Linux systems might send packets to port 137?

---

### Post by Doug S on 2017-03-02
I have only ever known port 137 stuff to be related to samba, but specifically the nmbd (NetBIOS name server to provide NetBIOS over IP naming services to clients). I have also typically found the packet interval to be ~5 minutes, however it seems to go to much longer if I disable services on my server.

---

