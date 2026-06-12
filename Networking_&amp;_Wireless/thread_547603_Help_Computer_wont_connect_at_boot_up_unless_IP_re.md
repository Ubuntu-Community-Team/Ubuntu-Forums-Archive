---
title: "Help: Computer wont connect at boot up unless IP refresh is done"
date: 2007-09-10
forum: Networking &amp; Wireless
---

### Post by vapore0n on 2007-09-10
I dont know what I did last week, but here is the result.

When I boo up the computer will get a dynamic IP as normal, but it wont do anything until the IP is refreshed.
What I do is switch to wireless and then back to wired. Or change from dynamic to static and back to dynamic. Then it starts to work.

Anyway to fix what I broke? What packages would I have to reinstall for networking?

Thanks

---

### Post by jnorthr on 2007-09-10
Is this for a wired modem or are you trying to get a wireless connection to work ?
you can try to restart the network with:

sudo /etc/init.d/networking restart

---

### Post by vapore0n on 2007-09-10
its for wired network. Local network

---

