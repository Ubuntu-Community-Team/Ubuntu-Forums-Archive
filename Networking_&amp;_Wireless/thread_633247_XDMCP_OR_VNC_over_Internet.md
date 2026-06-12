---
title: "XDMCP OR VNC over Internet"
date: 2007-12-06
forum: Networking &amp; Wireless
---

### Post by pbhat on 2007-12-06
I am not sure this question belongs here.This I think is the best place to ask.

When I am in IM with a friend,I want to connect to his computer using VNC or XDMCP.

He is behind another ISP in another country.I am also behind a ISP.But as we are already in touch,both the systems  already know each other.Now to do a VNC or XDMCP login,will it be right if I use the IP from whatismyip.com for both machines? Or else, how will I specify my friend's machine?

---

### Post by Friek on 2007-12-06
When you're using something like MSN, both boxes aren't communicating with each other. They're using the IM services' servers to exchange messages. 
When you want to connect to your friends box, you have to know his IP. Besides that, if your friend is behind a NAT router, he needs to have the needed ports forwarded to be able to connect from the outside.

I don't recommend xdm for slow connections. If either of you doesn't have lots of bandwidth, use VNC or even better: [NX](http://www.nomachine.com/).

---

### Post by pbhat on 2007-12-07
Thanks Friek.

I was wondering is there a technological equivalent of windows remote desktop in Linux.What I mean is this.I was browsing in an internet cafe and my friend from far could take control of my desktop and guide me about a thing.That was a similar situation and my friend and I did no port forawrding or something like that.

Parameshwara Bhat

---

### Post by gigaferz on 2007-12-09
yes it is possible.
but you need to do a few things before making it happen.
right now i can control my computers on my network using Terminal Server Client, then choose vnc. The other computer must have checked the box to allow remote desktop connection. is in system prefernces remote desktop.

but if you are behind a router, you need to configure your router to make it happen.

And if you want to control a windows machine that machine must have realvnc or ultravnc.

google up how to configure your router.

also is VERY convenient if under DHCP you make your IP address static. This is done in the router configuration page

in tips and tutorials there is a post  that says Hw to reverse vnc [http://ubuntuforums.org/showthread.php?t=299489&highlight=reverse+vnc](http://ubuntuforums.org/showthread.php?t=299489&highlight=reverse+vnc)

---

