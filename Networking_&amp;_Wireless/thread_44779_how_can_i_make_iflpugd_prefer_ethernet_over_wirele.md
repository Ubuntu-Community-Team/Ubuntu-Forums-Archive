---
title: "how can i make iflpugd prefer ethernet over wireless?"
date: 2005-06-27
forum: Networking &amp; Wireless
---

### Post by cell on 2005-06-27
Hello,

I setup my laptop with ifplugd, but if both wireless and ethernet connections are available, it creates a default route to both!

It appears that whichever interface happens to be configured first gets an entry in the route table first, and it gets used.

How can I make it prefer the route over ethernet?

I suppose what I need is some method of indicating which interface is my "preferred" interface, such that any time it becomes available, ifplugd first deletes the existing default route before adding the additional default route.  And, if the preferred interface is already up, it should prevent any other default routes from being added.

The reason I want this is because some wireless networks require you to "log in" via a website before they will route any packets for you.

Any ideas?

---

### Post by cell on 2005-06-27
hmm, perhaps I can do this in a round-about way using ifmetric:

[http://0pointer.de/lennart/projects/ifmetric/](http://0pointer.de/lennart/projects/ifmetric/)

---

### Post by cell on 2005-06-28
OK, there is a very simple way to do this using ifmetric.  I decided not to use ifplugd, and just use the network management tools which come with gnome (network-admin).

Create /etc/init.d/ifmetric:

--- cut ---
#!/bin/sh
/usr/sbin/ifmetric ath0 1
--- cut ---

Then add it to system startup just after networking comes up:

update-rc.d ifmetric start 41 S .

Viola

---

