---
title: "router and ufw"
date: 2015-01-08
forum: Networking &amp; Wireless
---

### Post by ELMIT on 2015-01-08
I got a router, which is connected to a fix IP address.

I use a desktop with some program, which I want to access from the wild Internet.

I have setup ufw:

sudo ufw status verbose
Status: active
Logging: on (low)
Default: deny (incoming), allow (outgoing), disabled (routed)
New profiles: skip

To                         Action      From
--                         ------      ----
80/tcp                     ALLOW IN    Anywhere
443/tcp                    ALLOW IN    Anywhere
12333/tcp                  ALLOW IN    Anywhere
80/tcp (v6)                ALLOW IN    Anywhere (v6)
443/tcp (v6)               ALLOW IN    Anywhere (v6)
12333/tcp (v6)             ALLOW IN    Anywhere (v6)


I have setup the router to forward all these ports to the pc.
80,443 seems to work. Port 12333 I cannot figure out why it does not.

Which tests can I make to tackle down this problem?

---

### Post by ajgreeny on 2015-01-08
Run command```
netstat -an | grep ':12333'
```in terminal to see if that port is listening or not. If not you need to try and figure out what is stopping it.

I am no expert in ufw so I don't think I can go any further, I'm afraid, but this may give you a start.

---

### Post by ELMIT on 2015-01-08
Thanks!

My router did not like to use "both". When I changed it to only TCP it worked. I confirmed it with [http://canyouseeme.org/](http://canyouseeme.org/)

---

