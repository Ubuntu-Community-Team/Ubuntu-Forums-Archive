---
title: "Wireless woes with 2.6.17"
date: 2007-04-19
forum: Networking &amp; Wireless
---

### Post by Cheekio on 2007-04-19
Here's a list of complicated symptoms of probably a hundred different problems. Maybe someone will be able to help, my laptop is almost unusable at this point, and the next step is either fix it or find a copy of a new operating system.

Alright, so I updated my kernel to 2.6.17 when it came out, thinking the newer the better. At the time I was running Edgy Eft 2.6.15....something, I think 23.

My beautiful, 80 dollar atheros wireless card (the side pcmia bus, I think that's the right term) stops working. Apparently 2.17 doesn't support madwifi anymore. I go ahead and boot 2.6.15 to do wireless work, and then, well, I didn't do anything. I kept booting 2.6.15 consistently, and have ever since. Otherwise the wireless card just doesn't work.

So I kept installing new updates Ubuntu suggested, and tonight I pull out the laptop after not using it for like a week. Boot 2.6.15, and for some reason half the wireless networks don't show up. Not even half- one shows up, the only unprotected 6% signal in town shows up. I run kismet, and it sees all sorts of traffic, but my drop down wireless menu just doesn't want to play ball.

So I click 'Enable Networking' on and off a dozen times and I start getting more signals, but not all of them. Eventually I do find my precious home signal, but consistently for as long as I've been running Ubuntu, if I don't get asked for the password to the key manager when I boot the laptop, I can input the wireless key by hand a hundred thousand times and it won't work. It will just sit and not get in.

I looked online and saw that 2.6.20 is apparently out, and I can't for the life of me figure out how to update to that kernel. Having no friends that use linux, I come here. Any ideas? It's a Dell Inspiron 600m, with an atheros card that the device manager calls AR5212 802.11abg NIC. And for the life of me I can't get it to check my email.

---

### Post by Cheekio on 2007-04-23
Damn, I figured this wasn't too hard to fix. Thanks or the views, I'll see if I can track down a ubuntu expert on campus.

---

