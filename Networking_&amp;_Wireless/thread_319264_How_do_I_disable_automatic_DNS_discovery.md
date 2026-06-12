---
title: "How do I disable automatic DNS discovery?"
date: 2006-12-15
forum: Networking &amp; Wireless
---

### Post by OneSeventeen on 2006-12-15
As I've mentioned in [this thread](http://ubuntuforums.org/showthread.php?t=313183) I am having issues where my laptop is always going out and finding great new DNS's, and for some reason sometimes when it gets the new DNS it completely ignores my hard-coded DNS servers, and the new DNS's rarely work, so I'm all of a sudden limited to only accessing IP addresses.

While it gets new DNS server IP's all the time, it rarely gets its own IP, so if I'm on a dynamic IP I have to remember to occassionally type "sudo dhclient" to get a new IP.

How can I disable the automatic DNS discovery and just use my static DNS servers?

Is it possible to have it renew my IP, basically doing the same thing as dhclient but automatic?

It takes an average of 5 minutes after boot to get on the internet with a proper DNS server and IP, then every 10 to 15 minutes (sometimes much shorter) I have to re-run dhclient, a few iwconfig and ifconfig commands, and manually edit /etc/resolv.conf before I can get back on the web again...

[size=1]**Edit:**
I've started this thread in addition because the other was a more generic "I have an issue" thread, and this is a specific "How do I disable dynamic DNS" thread, which will make it easier for people searching in the future, and will hopefully attract people who know how to disable dynamic DNS features in Ubuntu.  (just so you know I'm not merely spamming the forums)[/size]

---

### Post by Iowan on 2006-12-15
[http://ubuntuforums.org/showthread.php?t=317996]("http://ubuntuforums.org/showthread.php?t=317996")
This thread is plowing similar ground.
I presume the **domain-name-servers ** is gone from the **request** line in **dhclient.conf**?

> ...which will make it easier for people searching in the future...
Might also use/create a tag. DNS is ominous by it's absence.

---

### Post by OneSeventeen on 2006-12-15
Thanks for making me re-read that post Iowan!

Apparently even though we had different symptoms (he was able to ping google.ie, but I was not able to ping anything but IP addresses), the solution was the same, and that was to remove "domain-name-servers, " from the request line.

so my new /etc/dhcp/dhclient.conf reads:```
prepend domain-name-servers 208.67.222.222, 208.67.220.220;
request subnet-mask, broadcast-address, time-offset, routers,
        domain-name, host-name,
        netbios-name-servers, netbios-scope;
```

I'll post back in my previous thread about it dropping out every 30 minutes if this doesn't solve the issue.
> **Iowan said:**
> Might also use/create a tag. DNS is ominous by it's absence.
I'm not sure I follow you, should I have added a different tag other than what I submitted?  Or did my tags not get sent along with the post?

---

### Post by Iowan on 2006-12-15
> **OneSeventeen said:**
>  Or did my tags not get sent along with the post?
I didn't notice any tags, but I may have missed it/them.
(Or maybe the new format doesn't display them?)

---

