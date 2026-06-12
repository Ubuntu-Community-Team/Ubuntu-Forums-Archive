---
title: "Share VPN connection on home network?"
date: 2005-06-07
forum: Networking &amp; Wireless
---

### Post by cwaldbieser on 2005-06-07
My home network has two computers that share our normal Internet connection via a router.  From my Ubuntu machine, I am able to establish a VPN.  I can access the remote network just fine from my Ubuntu machine, but the VPN is not available from the second machine.

Is it possible to turn my Ubuntu machine into some sort of router that would et my second computer also access the VPN?  If so, what software would I need in order to accomplish this?  Are there any tutorials or HOWTOs that anyone could reccommend?

Thanks,
Carl

---

### Post by Arthemys on 2005-06-07
I believe something like that is feasable, however the correct way that I've been taught is that you'd want the router / NAT device to establish the VPN connection and that way it can route appropriately. If you wanted your ubuntu box to be a router you'd need to enable router support in your kernel if it hasn't been already and of course have a second NIC. This of course is where I start to falter in the area of knowledge. It does sound possible to do, but I wouldn't know the right way to go about creating a software router.

---

