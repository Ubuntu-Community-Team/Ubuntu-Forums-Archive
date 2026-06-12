---
title: "Changes to /etc/network/interfaces"
date: 2008-08-11
forum: Networking &amp; Wireless
---

### Post by MightyMartian on 2008-08-11
I've got myself in a bit of trouble with a remote computer running Ubuntu 8.04.1.  Initially I had had it set up for DHCP, but decided to go for a static address.  I alter the /etc/network/interface file and immediately upon saving it, I've been locked out.  The IP address hasn't changed, just the fact that it's static.  It's at a remote location so I'm kinda buggered right now, but why would the change be immediate, and if there's some daemon involved, how do I remove it?  That was the worst part about Cisco IOS configuration, and other flavors of Linux that I've used certainly don't suffer from this.

---

### Post by mrsudo on 2008-08-11
can you give us the contents of your interface file, then we can try and see whats wrong

---

### Post by Iowan on 2008-08-12
It does seem a bit unusual to have the change so immediate - usually requires restarting networking. Unlikely scenerio - lease timed out, wouldn't renew as static.

Oops, sorry for the dupe - trying to correct spelling.

---

### Post by Iowan on 2008-08-12
It does seem a bit unusual to have the change so immediate - usually requires restarting networking. Unlikely scenario - lease timed out, wouldn't renew as static.

---

