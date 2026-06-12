---
title: "Can not connect to local SSH, can from the outside"
date: 2015-11-19
forum: Networking &amp; Wireless
---

### Post by Vissie on 2015-11-19
Hi. I believe I have a odd and funny situation here. Not sure.

I have a ssh server setup and running on a non-standard port. Lets say port 1234 with ip address 10.10.10.99
I have a port forward on my router to allow traffic from the internet to reach that port.
I have a no-ip dynamic host name setup. Lets say name.no-ip.com.

From the internet I can ssh -p 1234 name.no-ip.com. Its works!
From my local LAN I can ssh -p 1234 10.10.10.99. Its works!
From my local LAN I can not ssh -p 1234 name.no-ip.com. Does not work.
From my local LAN I can ssh out to the internet. That works.

ssh: connect to host name.no-ip.com port 1234: Connection refused

From my local LAN I can PING name.no-ip.com and I get the correct external IP.

So it seem that only from my local LAN, something blocks traffic out.
Its not a ssh thing. If I telnet to name.no-ip.com 1234, same error.

Does anyone have any idea where I can try and look/find the issue?

Vissie

---

### Post by Lars Noodén on 2015-11-19
> **Vissie said:**
> 
From the internet I can ssh -p 1234 name.no-ip.com. Its works!
From my local LAN I can ssh -p 1234 10.10.10.99. Its works!
From my local LAN I can not ssh -p 1234 name.no-ip.com. Does not work.


What about ssh from the local LAN to the external IP address that name.no-ip.com currently resolves to?  If that does not work either then the problem may lie with the modem or router.  Not all of them support NAT hairpinnng.  

What model of modem or router are you using?

---

### Post by Vissie on 2015-12-01
> **Lars Noodén said:**
> What about ssh from the local LAN to the external IP address that name.no-ip.com currently resolves to?  If that does not work either then the problem may lie with the modem or router.  Not all of them support NAT hairpinnng.  

What model of modem or router are you using?

Hi. Good suggestion. But sadly I get the same response if I ssh to the internet IP directly "Connection refused".

My router is a TP-LINK AC1750 Wireless Dual Band Gigabit Router                  Model No. Archer C.
I have never in my live heard of "NAT hairpinnng". I will Google that a bit.

It seems odd and funny indeed. I'm wondering (as a work around) I can do some type of a local DNS that will translate my DyNa-DNS to a local IP.
But its odd. I'll like to know why, what is going on.

Vissie

---

### Post by Hadaka on 2015-12-01
hi,Lars ,who knows this stuff more than i do can correct me if im wrong.
from what i read it sounds like its doing exactly what its suppose to do
you cannot ssh yourself using the same router to connect to a machine within your 
local area network. lan, by sshing the port forwarded ip on the same lan. you have
proven that outside your lan..from the net..machine not attached to your router you can
connect to the port forwarded ip.
This would be correct and normal
```
From the internet I can ssh -p 1234 name.no-ip.com. Its works!
From my local LAN I can not ssh -p 1234 name.no-ip.com. Does not work
```
This also proves it is working correctly....name.no-ip.com..resolves to 10.10.10.99. 
```
Lets say port 1234 with ip address 10.10.10.99 
From my local LAN I can ssh -p 1234 10.10.10.99 Its works!
```
Perhaps you can do the hairpinning thing which i am clueless about to make it work "abnormal"

experts welcome to chime in if im not correct here.
thanks.

---

### Post by Vissie on 2015-12-01
Hi.
Now that I know what this issue is called "hairpinng", it makes resolving it easier. 
I found this:
[https://supportforums.cisco.com/discussion/11510056/hairpinning-or-nat-internal-internal-cisco-routers](https://supportforums.cisco.com/discussion/11510056/hairpinning-or-nat-internal-internal-cisco-routers) 

There they also agree that this behaviour is not a router issue, but a DNS issue. They also have a "work-around". 
I'll try that and see. Make sense.

Thx! I'll try and report back.

Vissie

---

### Post by Vissie on 2015-12-01
I'll keep you posted.

Vissie

---

