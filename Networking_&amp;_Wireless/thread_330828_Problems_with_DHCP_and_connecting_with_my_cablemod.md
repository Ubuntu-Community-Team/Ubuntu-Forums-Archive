---
title: "Problems with DHCP and connecting with my cablemodem"
date: 2007-01-03
forum: Networking &amp; Wireless
---

### Post by threethirty on 2007-01-03
Hi all, 

I'm having a terrible time getting by Dapper box to connect to the Internet.  I'm getting packets coming in but I'm not sending any.  I ran ifconfig and here is what i have under etho
```
eth0      Link encap:Ethernet  HWaddr 00:20:ED:87:24:21
          inet addr:10.79.2.14  Bcast:10.79.3.255  	        Mask:255.255.254.0
          inet6 addr: fe80::220:edff:fe87:2421/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4414 errors:0 dropped:0 overruns:0 frame:0
          TX packets:89 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:270120 (263.7 KiB)  TX bytes:9073 (8.8 KiB)
          Interrupt:177 Base address:0x8000

```

and i cant ping anything because it says it "unknown host"

any ideas?:confused: ](*,)

---

### Post by lloyd_b on 2007-01-03
Could you run the "route" command, and post the results?  Also, post the contents of the file "/etc/resolv.conf"?

You are getting a valid IP address, in the 10,x,x,x range.  DHCP *should* be setting a gateway for you, which will show as a "default" route in the route command.

If you see a "default" route, then try running this "ping 209.131.36.158" (that's the IP for Yahoo!).  If that gets a result, then your network connection is fine, but you have a problem with DNS (i.e. it's having problems looking up "www.yahoo.com" to determine that it's at 209.131.36.158).  The contents of "resolv.conf" should provide a clue in this case.

Lloyd B.

---

### Post by threethirty on 2007-01-03
resolv.conf has this

```
search insightbb.com
nameserver 74.132.1.130
nameserver 74.132.1.131

```

route shows this

[code] Kernal IP routing table 
Destination     Gateway        Genmask          Flags      Metric     Ref    Use   Iface
10.79.2.0         *               255.255.254.0   U            0            0      0     eth0
defualt           10.79.2.1      0.0.0.0             UG           0           0             eth0

and the ping hasn't returned anything all it says is

PING 209.131.36.15 (209.131.36.25) 56(84) bytes of data.

thanks for the reply

---

### Post by lloyd_b on 2007-01-03
> ```
Kernal IP routing table
Destination Gateway Genmask Flags Metric Ref Use Iface
10.79.2.0 * 255.255.254.0 U 0 0 0 eth0
defualt 10.79.2.1 0.0.0.0 UG 0 0 eth0
```

and the ping hasn't returned anything all it says is

PING 209.131.36.15 (209.131.36.25) 56(84) bytes of data.

That netmask is a little different than usual (I would expect 255.255.255.0), but they also set the broadcast at 10.79.3.255, so there appears to be a reason for it.

It is correctly setting a gateway (at 10.79.2.1), but something isn't working right. (note: "default" is misspelled in you message - I'm assuming that's a typo on your part).  You have a good static route (the "10.79.2.0 * 255.255.254.0... " line) telling the machine how to reach the gateway, so you *should* be able to reach the gateway.

Try "ping 10.79.2.1" - if this fails to respond, then the gateway that you're getting from DHCP is bogus. 

If the gateway does respond, then try the following:
"traceroute 209.131.36.25" and post the results - I'm curious as to whether or not you're getting beyond the gateway. (note: you may need to install the "traceroute" package for this to work).

Also, try "ping 74.132.1.130" and "ping 74.132.1.131" to see if either of the nameservers that it's giving you are accessible.  If the pings fail, try running "traceroute" on those addresses and see how far THAT gets.

Lloyd B.

---

### Post by threethirty on 2007-01-06
Ok it wasn't anything on my end.  My ISP hadn't changed my router from where I used to live.  Thanks for the replies.

---

