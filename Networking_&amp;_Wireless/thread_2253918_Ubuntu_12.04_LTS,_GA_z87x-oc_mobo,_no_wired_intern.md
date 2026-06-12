---
title: "Ubuntu 12.04 LTS, GA z87x-oc mobo, no wired internet connection"
date: 2014-11-23
forum: Networking &amp; Wireless
---

### Post by maurice8 on 2014-11-23
I just installed Ubuntu (spec in title) and everything seems to be working except for wired internet connection. I have attached the output from running the wireless_script, though I don't even have
a wifi card and have no desire to establish a wifi connection. So I don't know how much the output from that script will be useful.

Any ideas for how to get wired connection working? Any more information needed to figure out what to do?

Thanks everyone in advance!

---

### Post by jeremy31 on 2014-11-23
It appears that ```
nameserver 75.75.75.75
nameserver 75.75.76.76
``` is the issue.  Try setting DNS to google public 8.8.8.8 and 8.8.4.4

But it does seem that comcast is using DNSSEC

---

### Post by maurice8 on 2014-11-23
jeremy31, where do I change this setting? What will this do?

---

### Post by maurice8 on 2014-11-23
I went to IPv4 Settings, changed Method to Automatic (DHCP) addresses only, and added 8.8.8.8 to DNS servers, saved it, and tried again. Still nothing...

---

### Post by jeremy31 on 2014-11-23
You should be able to go into network manager and change wired connection properties, under the IPv4 tab you can add additional DNS

Can you ping IP addresses in terminal?  ```
ping -c3 8.8.8.8
```

---

### Post by maurice8 on 2014-11-23
I get a response such as:

PING 8.8.8.8 (8.8.8.8): 56 data bytes
64 bytes from 8.8.8.8: icmp_seq=0 ttl=46 time=34.391 ms
64 bytes from 8.8.8.8: icmp_seq=1 ttl=46 time=35.463 ms
64 bytes from 8.8.8.8: icmp_seq=2 ttl=46 time=35.466 ms


--- 8.8.8.8 ping statistics ---
3 packets transmitted, 3 packets received, 0.0% packet loss
round-trip min/avg/max/stddev = 34.391/35.107/35.466/0.506 ms

---

### Post by maurice8 on 2014-11-23
When I go to Network Connections, it shows one connection: Name: Wired connection 1, Last Used: never. Nothing appears to show that I am connected, but yet I can browse the internet now... I'm going to try restarting my computer and see if I maintain connection.

---

### Post by maurice8 on 2014-11-23
I am posting this reply on my machine, so I'm obviously connected to the internet. But when I click connection information, it says no vallid connections found... This is really disturbing me. Under Network connections, it still shows Last Used never for the one connection that it displays. How can this be when I'm obviosly online right now.

I want to make sure things are configured correctly as I would like to use this machine as a small server.

---

