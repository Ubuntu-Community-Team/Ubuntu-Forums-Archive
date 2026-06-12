---
title: "What is this &quot;avah&quot; business?"
date: 2007-06-05
forum: Networking &amp; Wireless
---

### Post by verevi on 2007-06-05
I have eth0:avah and simply eth0 when I run ifconfig.  The "avah" one shows an external IP even though I'm nat'ed behind my router.  Just curious what this is.  Thanks for the help.

---

### Post by mrsno on 2007-06-05
Hi verevi, Avahi is a free Zeroconf implementation, including a system for multicast DNS/DNS-SD service discovery. It allows programs to publish and discover services and hosts running on a local network with no specific configuration. For example you can plug into a network and instantly find printers to print to, files to look at and people to talk to. This is similar to what apple and now vista operating systems do to make sharing services easy. This is normal behaviour

Hope this helps

---

### Post by RHTopics on 2007-06-05
I have been curious about Avahi as well.

Are there any known security risks associated with Avahi?

---

