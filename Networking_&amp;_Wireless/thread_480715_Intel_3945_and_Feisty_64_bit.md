---
title: "Intel 3945 and Feisty 64 bit"
date: 2007-06-21
forum: Networking &amp; Wireless
---

### Post by warreng on 2007-06-21
Hi all,

I'm having problems with wireless using an Intel 3945 (in a Dell 830 Laptop).

Network Manager sees my network, but when I try to connect, it asks me for the WEP key then spins for a while before asking again. It never connects.

If I use ifconfig I can see the details of the card against eth1.

I've read that IPv6 might be an issue, so disabled it. I've also tried extending the DHCP timeout (a problem for others). So far, no luck.

I'd really appreciate some advice on how to get this going. I thought X was going to be the main problem on this machine, but having followed advice in other threads about patching the driver for X3100, that works a treat!

---

### Post by warreng on 2007-07-17
I've tried this on both Feisty and Gutsy, 32 bit and 64 bit. It works flawlessly on 32 bit, never on 64 bit. It's a real puzzle.

Does anyone have any idea what the problem might be here?

---

### Post by warreng on 2007-07-18
OK. I reinstalled and tried again. I get a success rate of about 50%. When it does connect, it stays connected and does not drop out. When it doesn't connect the symptoms are as before.

I think this may be a DHCP issue; I've read that the DHCP client may time out before it gets an IP address when running on 64 bit. I'm going to try increasing the DHCP timeout and see if that improves matters.

---

### Post by warreng on 2007-07-24
Well, I'm plowing a lonely furrow here. Changing the DHCP timeout had no effect other than to take longer to come back (which does imply that it's waiting for an address though - otherwise you'd think it would have no effect at all).

I also found threads talking about IPV6, but disabling IPV6 has no effect on the problem.

---

### Post by tgm4883 on 2007-07-24
Probably no responses because nobody knows.  I have an intel 3945 and use it with Feisty 64 bit and it works OOB.  I dont use WEP though, I use WPA2 Personal.

---

### Post by warreng on 2007-07-31
Makes sense. I chose this machine mostly because of Intel video / wireless and how well they generally work under Linux.

When it works it works perfectly (like now). I'm beginning to wonder if it's the router. Anyone know of compatibility issues with Belkin?

---

### Post by warreng on 2007-09-10
OK. It's definitely software. I tried a different router, but that had no effect. However I just tried Gutsy Tribe 5. It works flawlessly. No connection problems, and when connect there are no speed issues.

Tribe 5 also boots as a live CD on the Dell (Tribe 2 didn't - haven't tried any others). It also detected the video out of the box, which Feisty and Tribe 3 didn't.

Woo hoo!

Nice job everyone on Gutsy!

---

