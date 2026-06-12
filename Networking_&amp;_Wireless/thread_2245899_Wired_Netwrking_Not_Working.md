---
title: "Wired Netwrking Not Working"
date: 2014-09-26
forum: Networking &amp; Wireless
---

### Post by ts1971 on 2014-09-26
Hi,

I've been using Ubuntu 14.04 for several weeks without any problem.  The internet connection is a wired connection.  The model is cable and the Ubuntu box is behind a Lynksys router.  All of the networking stuff has always just worked since the initial installation.  In an effort to get my feet wet with Wireless networking on Linux (so that I can take this laptop with me when I travel, I did the following:

(1) Shutdown ubuntu system
(2) Unplug network cable
(3) Restart ubuntu system
(4) Poke around some networking menus
(5) Shutdown ubuntu system
(6) Plug in network cable
(7) Restart ubuntu system

And now even my wired network isn't working.  It's possible that I inadvertantly made some changes when I was poking around the network stuff, but I don't think so.  I really can't imagine what I've done to hose my connection, but I'm desparate to get it back up and running.  I'm really not sure how to troubleshoot this, but I'll throw this out there as a start:

frank@frank-ThinkPad-T540p:~$ /sbin/ifconfig
eth0      Link encap:Ethernet  HWaddr 54:ee:74:24:f4:b0  
          inet6 addr: fe80::56ee:74ff:fe24:f4b0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:704 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:153175 (153.1 KB)
          Interrupt:20 Memory:f1600000-f1620000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:853 errors:0 dropped:0 overruns:0 frame:0
          TX packets:853 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:63207 (63.2 KB)  TX bytes:63207 (63.2 KB)

If anyone could point me in the right direction, I'd really appricate it!

Thanks.

---

### Post by TheFu on 2014-09-27
[http://blog.jdpfu.com/2013/03/01/linux-troubleshooting-101-networking](http://blog.jdpfu.com/2013/03/01/linux-troubleshooting-101-networking) hope this helps.
Also, please use "code" tags so things line up nicely.

---

### Post by varunendra on 2014-09-28
If the link given by TheFu doesn't help solving the problem, please follow the instructions in this post to download and run 'wireless_script' (experimental version) and post back the report it generates : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222)

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Use Code Tags" link in my signature.


**@TheFu,**

I still can access your blog only through proxy servers, not directly.
Thought I should keep you informed of the (no-)update. :p

---

