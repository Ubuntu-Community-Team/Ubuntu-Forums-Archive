---
title: "Howto ENABLE IPv6?"
date: 2007-04-21
forum: Networking &amp; Wireless
---

### Post by deadspider187 on 2007-04-21
I see a lot of howto's on how to disable ipv6, but I want to try out a ipv6 network.  My router is running a 6to4 tunnel via openwrt, but I still cannot ping6 [www.kame.net](www.kame.net)

```
deadspider187@aftermath:~$ ping6 www.kame.net
connect: Network is unreachable
deadspider187@aftermath:~$
```


the module ipv6 is loaded, as well as all of the ipv6 modules just to be safe.

---

### Post by Joe_Bishop on 2008-04-21
same problem

---

### Post by wannadumpwindows on 2008-04-21
Open firefox, and in the address bar type
```
about:config
```
and search for ipv6. Change the value to allow ipv6.

And actually, I thought it was enabled by default. I know it is on all of my machines, and I never had to enable it.

---

### Post by wannadumpwindows on 2008-04-23
Did that work for you, or are you still out in the icy cold webless world? If it fixed your problem, you should mark the thread as solved. If not, then ask away . . . . . .:)

---

### Post by broquea on 2008-04-24
I'm running 7.10 in my colo and at home. One as a VE under OpenVZ at a colo provider with native IPv6, and another at home using a [http://tunnelbroker.net](http://tunnelbroker.net) tunnel (since Comcast doesn't provide native IPv6).

In /etc/network/interfaces (sanitized):

iface venet0 inet6 static
        address ::1
        netmask 128
        up ifconfig venet0 add a:b:c::d

A non-virtual config could look like:

iface eth0 inet6 static
        address a:b:c::d
        netmask 64
        gateway a:b:c::1

If your OpenWRT is running RADVD then machines should be getting their IPv6 IP from them. I suppose it depends on what kind of addressing you get from your tunnel. I get a /64 routed to my side of the tunnel, and use that for the LAN.

---

