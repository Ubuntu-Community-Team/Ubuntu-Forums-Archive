---
title: "Port forwarding - additional options"
date: 2016-01-21
forum: Networking &amp; Wireless
---

### Post by recalcitrant on 2016-01-21
Greetings exalted ones :)

I don't know where to post my question so I choose The Cafe. My question concerns networking in general. 
There are two options when forwarding ports in some routers "_internal_: start port, end port" and "_external_: start port and end port" 
 I don't understand why there are *internal* and *external* - what do they mean. What is more these options are not in every router. What is the difference between *external* and *internal*? Why do some routers have them?

thanks

PS
I know how to configure the router I just don't know the meaning *external* and *internal*

---

### Post by pqwoerituytrueiwoq on 2016-01-21
external is what your router is listening to, internal is where it sends it to, if you only want to use one port, use start=80 and end=80

lets say you sent external port 6541 and internal port as 80
from inside your local network your address is [http://192.168.1.5/](http://192.168.1.5/) from outside it is [http://XXX.XXX.XXX.XXX:6541](http://XXX.XXX.XXX.XXX:6541) (where XXX.XXX.XXX.XXX is [your ip address](https://www.google.com/search?client=ubuntu&channel=fs&q=waht+is+my+ip&ie=utf-8&oe=utf-8))

---

### Post by slickymaster on 2016-01-21
> **recalcitrant said:**
> Greetings exalted ones :)

I don't know where to post my question so I choose The Cafe. <---snip--->

Hi recalcitrant, welcome to the forums. The proper venue for your thread his the **Networking & Wireless** sub-forum, to where I moved it.

---

