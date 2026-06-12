---
title: "Problem with Wireless in Ubuntu 8.10, ath5k driver"
date: 2008-11-15
forum: Networking &amp; Wireless
---

### Post by ximian153 on 2008-11-15
First off, hello. This is my first post, and I am a certified Ubuntu newbie. However, I do have capable help from my dad and brothers. Now for the problem:

So I got a new laptop, and we immediately set it up to dual boot Ubuntu 8.10 or Vista. Initially the problem with wireless was simply trying to get the right driver installed and working. We finally were able to find our solution with the ath5k driver. Success! However, as soon as we tried using the driver, it would work fine for about 10 seconds, then turn into an absolute crawl or stop working all together. 

I tried to ping google, and here is the result:

justin@justin-Laptop:~$ ping [www.google.com](www.google.com)
PING [www.l.google.com](www.l.google.com) (209.85.171.99) 56(84) bytes of data
64 bytes from cg-in-f99.google.com (209.85.171.99): icmp_seq=1 ttl=241 time =26.9 ms
64 bytes from cg-in-f99.google.com (209.85.171.99): icmp_seq=2 ttl=241 time =27.6 ms
64 bytes from cg-in-f99.google.com (209.85.171.99): icmp_seq=3 ttl=241 time =27.8 ms
64 bytes from cg-in-f99.google.com (209.85.171.99): icmp_seq=4 ttl=241 time =30.5 ms
64 bytes from cg-in-f99.google.com (209.85.171.99): icmp_seq=5 ttl=241 time =27.1 ms
64 bytes from cg-in-f99.google.com (209.85.171.99): icmp_seq=6 ttl=241 time =25.2 ms
64 bytes from cg-in-f99.google.com (209.85.171.99): icmp_seq=7 ttl=241 time =30.1 ms
64 bytes from cg-in-f99.google.com (209.85.171.99): icmp_seq=8 ttl=241 time =38.9 ms
64 bytes from cg-in-f99.google.com (209.85.171.99): icmp_seq=9 ttl=241 time =28.4 ms
64 bytes from cg-in-f99.google.com (209.85.171.99): icmp_seq=10 ttl=241 time =27.7 ms
ping: sendmsg: No buffer space available
ping: sendmsg: No buffer space available
ping: sendmsg: No buffer space available
ping: sendmsg: No buffer space available
ping: sendmsg: No buffer space available
ping: sendmsg: No buffer space available
ping: sendmsg: No buffer space available


The first 10 pings or so went fine, but then it would stall for a good 10 seconds, and then spit out "ping: sendmsg: No buffer space available" every second thereafter. 

Any help? Thanks!

---

### Post by ximian153 on 2008-11-17
Anyone? Help??

---

### Post by ximian153 on 2008-11-18
Is anyone here?! What's going on? I'd *really* like to get Ubuntu working, please help!! 

If you need more information, just ask! I'm trying my best to describe the problem...

---

### Post by Aearenda on 2008-11-18
There seem to be a number of similar threads in the forums, which I assume you have already looked at - just search for 'ath5k' if not. Also, have you Googled 'ping: sendmsg: No buffer space available'? Some of these suggest a hardware issue - but presumably it works with Vista.

What other software have you added to you installation that was not included by default?
How did you install the ath5k driver?

It would be useful if you post the output from the following commands:```
lspci
cat /etc/modules
cat /etc/modprobe.d/blacklist
lsmod | grep ath
```
I can't promise to be able to help, but this will be a start.

---

### Post by ketnave on 2008-11-30
Hi,

I am facing the similar issue.

I just setup ubuntu 8.10 on my Toshiba Satellite L310-N406, everything seems to work fine, with the exception of the wireless (extended display and log out user;which change my theme when i log back in).

The wireless work out of the box, but when I transmission for BT, after a few hours (i guess), the wireless would just stop working.

Pinging my router will result in "no buffer space"

I have added pci=noacpi to the boot option, but it doesn't solve the issue and I do not have the "no buffer space" message, instead, the ping would just froze.

I really does hope that someone can help me.

Thanks.

---

### Post by Aearenda on 2008-11-30
ketnave: There is no wireless adapter showing in your lspci output, but I suspect you should have an Intel wireless adapter in that laptop. Please start a new thread for your problem, including the output from lspci and lshw when the wireless is working.

---

