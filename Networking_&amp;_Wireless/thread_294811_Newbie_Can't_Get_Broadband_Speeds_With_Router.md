---
title: "Newbie Can't Get Broadband Speeds With Router"
date: 2006-11-07
forum: Networking &amp; Wireless
---

### Post by shafty1968 on 2006-11-07
Hi guys,

I'm really new to linux, so please go easy!

I have Ubuntu 6.06 installed on my laptop and have just hooked up a Dynamode R-ADSL-C4W-EG router via ethernet; however my connection speed to the net is about as the same speed, if not slower than dial-up.

I have gone into Firefox and disabled IPV6; things are now a bit faster, but not much.

I have DNS settings fro my ISP but everybody (including my ISP) has told me I don't need them and all I need is my ISP username and password.

Could anybody please offer some idiot-proof, newbie friendly advice?

Thanks very much in advance..

Cheers

BTW, when I access the net via Windows via the same ehernet router my connection speed is fine

---

### Post by stream303 on 2006-11-10
The speed issue sounds like dns timeouts (pages taking forever to load or not loading at all)

I'd check your **/etc/resolv.conf** file, and make sure it has your isp's dns nameservers listed at the top.  If not, perhaps this howto will help:

[http://www.ubuntuforums.org/showthread.php?t=282034&highlight=resolv.conf](http://www.ubuntuforums.org/showthread.php?t=282034&highlight=resolv.conf)

Lets see how this goes...

---

