---
title: "gateway setup"
date: 2007-09-30
forum: Networking &amp; Wireless
---

### Post by Tanchistu on 2007-09-30
I have entered the gateway in that applet but when I type:

radu@radu-desktop:~$ sudo route

I get:

Kernel IP routing table
Destination Gateway Genmask Flags Metric Ref Use Iface
81.181.8.192 * 255.255.255.192 U 0 0 0 eth0

so no gateway, [here]("http://linux.die.net/man/8/route") it says:

"route add default gw mango-gw
    adds a default route (which will be used if no other route matches). All packets using this route will be gatewayed through "mango-gw". The device which will actually be used for that route depends on how we can reach "mango-gw" - **the static route to "mango-gw" will have to be set up before.**"

so, how do I set the gateway, or how do I set "mango-gw?

thank you

---

### Post by noob12 on 2007-09-30
I responded to this on your original thread, did you try that?  [http://ubuntuforums.org/showthread.php?t=563381](http://ubuntuforums.org/showthread.php?t=563381)

---

