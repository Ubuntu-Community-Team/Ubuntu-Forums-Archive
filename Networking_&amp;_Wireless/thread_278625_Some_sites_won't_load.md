---
title: "Some sites won't load"
date: 2006-10-16
forum: Networking &amp; Wireless
---

### Post by nietorigineel on 2006-10-16
Hi there,

Some internet sites just won't load. I have seen the other posts concerning ipv6, and have that disabled. Still for example [www.hotmail.com](www.hotmail.com) changes into this long address ([http://login.live.com....etc](http://login.live.com....etc)) but than just doesn't load. No error messages, just a blank screen. [www.geenstijl.nl](www.geenstijl.nl) is another example.

If i ping, it does have an ip-address connected, but does not succeed.

What could be the problem?

---

### Post by nietorigineel on 2006-10-17
*bump*

keep on finding more sites that don't work, what's this all about? I run a dualboot with XP, also with opera, and all is fine there.

---

### Post by unprinted on 2006-12-05
I'm a bit surprised not to find more complaints like this, because, yes, live.com (and therefore now hotmail.com) won't load for me here either.

(And neither will the .nl site you mention, but I haven't spotted any others.)

I'm at work at the moment - I'll see what the two machines at home are like.

---

### Post by unprinted on 2006-12-05
Hmm, it works ok at home.

Work: Ubuntu 6.06 and 6.10 via a Netgear DG632 router to Easynet.

Home: Ubuntu 6.10 via HomeChoice.

No obvious other differences, and neither site responds to pings from either location.

---

### Post by unprinted on 2006-12-06
> **nietorigineel said:**
> I run a dualboot with XP, also with opera, and all is fine there.

This is interesting, because I brought my dual boot home laptop into work today. It will access hotmail fine at home, but not here, regardless of whether it's XP Pro or Ubuntu 6.10.

Wierd...

Next step is to try swapping the router, just to see if that's the problem.

---

### Post by eXisor on 2006-12-06
This sounds like an MTU problem. 

Use a tool like TCPOptimiser or Drtcp (both windows unfortunately) to check what should be the optimal MTU for your ISP. Once you get that, set your router to the optimal, and then your various machines.

Ubuntu and windows both set MTU to 1500, which may cause excessive packet fragmentation, and hence the page will just not load.

Since it works fine at home, and not well at work, it tends to support my theory that it is an mtu problem. Try dropping mtu down to 1452, or even as low as 1352 and see if it helps.

(You set mtu in the /etc/network/interfaces file)

---

### Post by unprinted on 2006-12-07
> **eXisor said:**
> Since it works fine at home, and not well at work, it tends to support my theory that it is an mtu problem. Try dropping mtu down to 1452, or even as low as 1352 and see if it helps.

Thanks. 

Hmm, well this morning I was able to try another router and it works with that, so it's not inherent to the setup of the PCs.

The problematic router is known to have some other problems (it doesn't pass DNS servers correctly via DHCP, so they have to be set up manually).

Once I can stand to be separated from a M$ service :) I'll try the old one again, twiddle away and see what happens.

But my basic cure will be to tell the IT department to get us a new router.

---

### Post by unprinted on 2006-12-07
> **unprinted said:**
> I'll try the old one again, twiddle away and see what happens.

Well, it works now :)

Curiously, the 'bad' router had MTU set at 1452, and changing that to 1500 has cured this problem. 'Yay!' and 'Huh?' at once :)

Will this have caused the other problem, I wonder, if the PC and the router have different MTUs?

Thank you.

---

### Post by eXisor on 2006-12-08
AFAIK all devices in the chain need to have the same mtu, else packet fragmentation occurs between the devices.

---

