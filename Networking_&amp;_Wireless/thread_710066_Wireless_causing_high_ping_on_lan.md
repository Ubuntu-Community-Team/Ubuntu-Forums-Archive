---
title: "Wireless causing high ping on lan"
date: 2008-02-28
forum: Networking &amp; Wireless
---

### Post by genbuntu on 2008-02-28
Hi

I have noticed that whenever the wireless connection is used , it causes v. high ping on the lan connected computers (All on a single router home network). :confused:
The router I use is: Trendnet TEW 432BRP. 

The ping command yields the following statistics: 
```
 PING google.com (64.233.187.99) 56(84) bytes of data.
64 bytes from jc-in-f99.google.com (64.233.187.99): icmp_seq=1 ttl=241 time=763 ms
64 bytes from jc-in-f99.google.com (64.233.187.99): icmp_seq=2 ttl=241 time=578 ms
64 bytes from jc-in-f99.google.com (64.233.187.99): icmp_seq=3 ttl=241 time=625 ms
64 bytes from jc-in-f99.google.com (64.233.187.99): icmp_seq=4 ttl=241 time=563 ms
64 bytes from jc-in-f99.google.com (64.233.187.99): icmp_seq=5 ttl=241 time=498 ms
64 bytes from jc-in-f99.google.com (64.233.187.99): icmp_seq=7 ttl=241 time=725 ms
64 bytes from jc-in-f99.google.com (64.233.187.99): icmp_seq=8 ttl=241 time=568 ms
64 bytes from jc-in-f99.google.com (64.233.187.99): icmp_seq=10 ttl=241 time=538 ms
64 bytes from jc-in-f99.google.com (64.233.187.99): icmp_seq=11 ttl=241 time=465 ms

--- google.com ping statistics ---
12 packets transmitted, 9 received, 25% packet loss, time 17626ms
rtt min/avg/max/mdev = 465.389/591.862/763.367/92.777 ms
 
```

When wireless is not in use, the pings are usually around 30 ms. Why is this happening and any ideas/suggestions to resolve this problem? Thx.

Edit: I've also tired reducing the transfer rate to 1 MBps (default: 'Auto')  and changed the beacon interval to 1000 (default: 100) in the wireless section of my router's configuration page, but that didn't help :( .

---

### Post by jhetrick62 on 2008-02-28
Does that really change your browsing experience?  If not, don't worry.  If it truly slows the machine down, the driver most probably isn't perfectly compatible would be my guess, or the router just isn't handling this as efficiently as it should.

Do you ever take the machine to another wireless network?  What happens then with the ping responses?

Jeff

---

### Post by genbuntu on 2008-02-28
> **jhetrick62 said:**
> Does that really change your browsing experience?  If not, don't worry.  If it truly slows the machine down, the driver most probably isn't perfectly compatible would be my guess, or the router just isn't handling this as efficiently as it should.

Do you ever take the machine to another wireless network?  What happens then with the ping responses?

Jeff

Yes, it indeed slows down the browsing i.e. page loading , log in 's  etc.  Also, severely effects my VoIP phone quality. :(

The ping returns to normal whenever I switch off the wireless connection. 

I'm suspecting the router's handling abilities and thinking of changing the firmware . While doing some research on this, I came across , what seems to me , a v. interesting option to replace my router's proprietary firmware with an open-source one ( like OpenWrt : [http://openwrt.org/](http://openwrt.org/) )  :) . The idea seems to have caught my attention so I'm keen on trying it out. 
However, I'd like to know others' opinion on this and whether OpenWrt is the best one out there? or are there any better (more widely used or stable) than this. ? 
All help/suggestions/links are welcome . :KS

---

