---
title: "Slow, Sporadic, Nonexistent Internet"
date: 2007-06-29
forum: Networking &amp; Wireless
---

### Post by ryP on 2007-06-29
Just wanted to throw this out there as more of a reference than anything.  I am completely new to Ubuntu/Linux and was really digging it.  But my internet was killing me; completely sporadic, and always super slow, couldn't connect to some sites at all.  2 XP machines on same network were fine.  After scouring these forums I found a wealth of info on various possibilities.  I disabled IPV6 both system wide and in firefox, but that did nothing for me.  Swapped routers, connected directly, still nothing.  After reading a couple posts on tcp window scaling, that seemed to fit my symptoms perfectly.  But I tried a couple of the fixes I could find and they didn't really help either.  Anyway, I found this good page on the internets the other day and just wanted to put it out there in case anyone was having the same problem I was.  The link is:

[http://www.santa-li.com/linuxonbb.html](http://www.santa-li.com/linuxonbb.html)

I guess there a a few different ways to get to this end result but what I ended up doing was just replacing the contents of my \etc\sysctl.conf file (after saving off a copy of course) with the following (and this is just copied from the site):

net.core.rmem_default = 524288
net.core.rmem_max = 524288
net.core.wmem_default = 524288
net.core.wmem_max = 524288
net.ipv4.tcp_wmem = 4096 87380 524288
net.ipv4.tcp_rmem = 4096 87380 524288
net.ipv4.tcp_mem = 524288 524288 524288
net.ipv4.tcp_rfc1337 = 1
net.ipv4.ip_no_pmtu_disc = 0
net.ipv4.tcp_sack = 1
net.ipv4.tcp_fack = 1
net.ipv4.tcp_window_scaling = 1
net.ipv4.tcp_timestamps = 1
net.ipv4.tcp_ecn = 0
net.ipv4.route.flush = 1

Then run the following command to have it take affect immediately:

sysctl -p

You can just add this stuff to the end of the file if you want, if you have other settings in there. My default sysctl.conf file was all commented out anyway, so I just scrapped it.  After doing this, I am absolutely flying right now.  As the page says, you may want to tweak your max window size if this doesn't work for you as setting a lower window size may work better with your ISP. 

I apologize if this is already out there, it must be the one entry I didn't read.  I was on the verge of scrapping Ubuntu as this was killing me, but this pulled me back, hope it can do the same for someone else.

---

