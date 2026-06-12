---
title: "Can't access home web server from at home"
date: 2014-01-13
forum: Networking &amp; Wireless
---

### Post by sliberty on 2014-01-13
I have a Linux machine running Apache at home. I use ZoneEdit to  provide a URL for my webserver. I use port forwarding in my router to direct requests to the right internal machine. People who access this web server from outside my home have no issues. My router is an ASUS RT-AC68U.
But while I am at home, I can't access my web server via the URL. I can however access it if I use the internal IP address (192.168.x.y). I have read that the problem might be related to DNSand that a split-DNS would solve it, but I am hesitant to set up a DNS server on my LAN (not an expert on these things).
Anyone have a simpler solution to this problem?

---

### Post by tfrue on 2014-01-13
Can you access the server from outside your home, and why not just use the private IP (internal)? If it works, don't break it. You connected to the LAN that your sever is on and you are trying to get access to it by going on the internet  back to your server that is on the same LAN you are on. I'm sure there are ways around it, but why?

---

### Post by ZippyUbu on 2014-01-13
Hi - I assume you are running Ubuntu on a Desktop? Not very elegant but  you could modify the host file on the machine. This would allow you to  use the external DNS link and it would resolve to your webserver. The issue is that if you are using a laptop and take it outside your LAN your website address won't resolve. (as it's looking at your host file)

Other options you may want to explore are that your router has a DNS proxy service on it that you might be able to do something with - Aside form that, a DNS server ...

LAN - 192.168.x.y - Webserver

Add this to your /etc/hosts file: ```
192.168.x.y    mywebserver.com
```

--
Zu

---

### Post by TheFu on 2014-01-13
> **tfrue said:**
> Can you access the server from outside your home, and why not just use the private IP (internal)? If it works, don't break it. You connected to the LAN that your sever is on and you are trying to get access to it by going on the internet  back to your server that is on the same LAN you are on. I'm sure there are ways around it, but why?

Some applications rewrite the URLs based on a setting, so to access the server in any useful way, the same URL must be used by all clients.
Modifying the /etc/hosts can work.  That is probably the easiest. Sometimes validating the routing and filtering is also part of the testing, so going through the WAN interface on the router is important.  I'd guess there is some "security" setting in the router that prevents this function - something like it might be part of an attack technique, I'd guess.

I've never heard of those other programs, so I can't say anything about what they are doing.  I know that dd-wrt, tomato, openwrt and pfsense routers do not usually display the problem you are seeing.

---

### Post by tfrue on 2014-01-13
I see, thanks for the info!

---

