---
title: "internet slow"
date: 2006-07-29
forum: Networking &amp; Wireless
---

### Post by stairwayoflight on 2006-07-29
hey everyone!!

-i am using ubuntu dapper 6.06 lts
-i access the internet through a router, it is firewalled, no proxy
-i have set certain ports to be fwd'd, perhaps the wrong ones, for bittornado


here's the prob:

-i have fast cable internet, but sometimes things are SLOW
-usually the web is lightning fast, but sometimes after using bittornado or while using it firefox can't find the server i am looking for (eg. google)
-bittornado itself is sometimes slow (tho i am working on that)
-rebooting and using firefox rectifies the problem (ie. web is fast)

i tried using ports ~ 30000 or so, and had this problem. i moved to ~ 6880 and thereabouts, still have the problem. i thought maybe i was using a port necessary for web traffic, but not sure. i thought bittornado was using up too much bandwidth (it hardly downloads at all ~0-5kb/s) but even after turning off bittornado i can't access the web sometimes. my only thought is its doing something to my connection/ports/whatever.

can anyone help??

---

### Post by rowanparker on 2006-07-29
Are you using a router?

---

### Post by calx on 2006-07-29
Try entering your ISP's DNS server address in your network settings.

---

### Post by stairwayoflight on 2006-07-29
> **calx said:**
> Try entering your ISP's DNS server address in your network settings.

sorry, i don't know what you mean.

have a router, receives all that from the dhcp server over wan, then acts as dhcp server over lan, to which my network card is connected. to put the dns server ip directly in my network settings, don't i have to discard the router? i am sure my router is my dns server, and in turn uses the isp's dns server.

is this wrong?

---

### Post by rowanparker on 2006-07-29
Have you opened the correct ports?

---

### Post by stairwayoflight on 2006-08-04
hi,

sorry for the delay.

i don't know what you mean by "correct ports." i assume you mean forwarding the correct ports through my router? i am forwarding the ports i have set up in bittornado, etc. i don't know anything about that, other than that i got the numbers to match up. i am correct in thinking there are specific ports for specific kinds of packets, and therefore there are some i should not be using, right?

but i end up getting the same results whether my ports for bittornado are ~30000 or ~6890. firefox can't find the servers for web pages.

---

### Post by stairwayoflight on 2006-08-06
hi,

well, parents are gone for the week. i don't have to worry about their net access so i unplugged the router now i'm hooked up to the cable modem directly.

the net speed is fine now, and bittornado downloading is much faster.

i wish i knew how to set things up with the router though. it was a cheapie, blanc networks for $2.99 after rebates. i hope it can handle the bandwidth? i guess a worthy experiment would be to put the router back in, then disable the firewall and see how fast it is. i'll try it when i have time.

---

### Post by stairwayoflight on 2006-08-13
well things have been faster with the router removed. but that leaves the box upstairs with no net. i must reconnect it.

anyways, to recap i have a router, all the ports i am using for p2p are set up in the port forwarding settings, but things slow down quite a bit and sometimes the web is inaccessible. sometimes it can take 30 - 60 sec's for a web page to come up with fast cable access.

does that sound like the router is slowing down? can it be its too many connections for it to stay full speed?

---

### Post by kvlastos on 2006-08-13
I am having same problem for last 2 days on more than one distro. I have tried shutting down firewll, rebooted the router, etc. The problem is that when looking for a web address, it takes roughly 13 minutes to retrieve the page. Once on a particular web server site, it is fine and goes through the pages quickly. Before, it was fine and Linux was faster than my XP boxes.

The strange thing is that the process doesn't time out. Normally, if the web address does not respond very quickly, a time out is sent. Yet, now it just hangs for about 13 minutes, finally loading the page. Now, my cable hi-=speed is slower than dialup.

The XP discs work normally. I am running 6.06.1 and SUSE 10. Noemally, they fly, but now something is amiss. If you get a fix, let me know. I have rebooted, reconfigured DHCP and I am at a loss.

Also, a PING from console reaches Google in about 13ms, so I may have a router problem that I do not see yet. Traceroute is very slow and the first 6 or 8 hops are obscured.

If you get a fix, let me know and thanks. Sorry I can't help.

---

### Post by kvlastos on 2006-08-14
forget it!

---

### Post by NetworkGuy on 2006-08-14
> **stairwayoflight said:**
> i guess a worthy experiment would be to put the router back in, then disable the firewall and see how fast it is. i'll try it when i have time.

Did you ever get a chance to do this?  It would help to troubleshoot the issue.

---

### Post by stairwayoflight on 2006-08-14
whadyamean, forget it! you mean you fixed it? i found a thread around that reccommended disabling ipv6 somewhere i think, search for "internet slow" and you'll find it

---

### Post by stairwayoflight on 2006-09-04
Hi,

I have reinstalled ubuntu since this problem and it has changed. Internet speeds (web/wget/apt-get/p2p) are all fine. But when I use bittornado, web surfing is very slow from then on, sometimes i can't get a page.

I am using DHCP for network settings. I have found if I leave bittornado running, it will dl my stuff, then I can shut it down to use the web and open the 'Networking' dialog under "System" in the gnome menu, click on "eth0" then the deactivate button, then activate. Browsing and all that work great after.

Is there any way to get them to work at the same time? I'm not sure what the problem is.. :-(

---

### Post by BlacKat_K on 2006-09-04
I have a slow internet problem too but it seems closing Kopete puts in back into speed...How annoying,i dont like Gaim so i'm stuck with this??

---

### Post by CGW on 2006-09-04
I was having the same problems--slow internet with Ubuntu but not with XP.  I upgraded the firmware in my router and everything works fine now.

---

