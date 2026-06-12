---
title: "lost internet connection"
date: 2011-01-07
forum: New to Ubuntu
---

### Post by kcfd25 on 2011-01-07
I have 2 ethernet ports on my computer.  One is a wired connection to my router, the other is hooked up directly to the PS3.  I turned on my PS3 and after turning it back off cannot get on the internet on my computer.  I don't know what went wrong.  I just hooked up my PS3 for the first time to my computer.  Been running ubuntu 10.10 for only a few months so I'm still a noob.  I'll post parts of my ifconfig below.  I can't copy and paste as I'm on my laptop.  Thanks.

etho  everything appears ok, no errors


lo Link encap: local loopback
inet addr:127.0.1 mask:255.0.0.0
inet6 addr:  ::1/128 Scope:Host
UPLOOPBACK RUNNING MTU:16436   Metric:1
Rx packets:604 errors:0 dropped:0 overruns:0 frame:0
TX packets:604 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txquelen:0
RX  bytes:89786 (89.7 kb)  TX bytes:89786 (89.7kb)

---

### Post by Bucky Ball on 2011-01-07
Did you recently upgrade your kernel?

---

### Post by kcfd25 on 2011-01-07
Well it looks like I got it figured out.  I just changed my ipv6 to ignore.

---

### Post by Bucky Ball on 2011-01-07
That's gonna do it! Good work. ;)

Please mark as 'solved' from 'thread tools', enjoy your new OS and the learning curve, and post back in a new thread with any other problems.

---

### Post by kcfd25 on 2011-01-07
It looks like its doing it again after turning on my PS3 again.  Ubuntu says its not connected.  I remember messing with some ipv6 settings in Firefox.  Don't remember which ones.  The reason being, Im trying to share a internet connection with my PS3.  Thanks

---

### Post by Bucky Ball on 2011-01-07
In Firefox address bar:

about:config

Then search for IPv6. That should give you:

network.dns.disableipv6

Set that to 'True'.

---

### Post by kcfd25 on 2011-01-07
Just did that and its still not working.  It was at False so I must have changed that when I was trying to set up my PS3.  Thanks for your help Bucky.

---

### Post by kcfd25 on 2011-01-07
Looks like its working again.  I just disable ipv6 in the grub and then updated it.  Scared to turn on my PS3 now.  LOL.

---

### Post by kcfd25 on 2011-01-07
I made a little progress.  I disabled ipv6 in the grub and then updated it.  Firefox now only works in offline mode.  I can go to any website but can't search with google or yahoo.  Also, it still shows no connection in the corner of my desktop.

---

### Post by kcfd25 on 2011-01-08
Figured out the problem.  I just shut everything down and unplugged  everything.  It has something to do with my PS3 being connected to my  onboard ethernet.  As soon as I turn it off the internet stops working.   I'm basically trying to use on NIC for internet and one as a local  link.

---

