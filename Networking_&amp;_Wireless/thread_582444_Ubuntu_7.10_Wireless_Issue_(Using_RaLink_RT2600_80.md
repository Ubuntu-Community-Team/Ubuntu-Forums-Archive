---
title: "Ubuntu 7.10 Wireless Issue (Using RaLink RT2600 802.11 MIMO)"
date: 2007-10-19
forum: Networking &amp; Wireless
---

### Post by AdHavoc on 2007-10-19
I just upgraded to Gutsy Gibbon, and so far, I haven't been able to get my RaLink RT2600 connected to my linksys router.  The router shows up fine, but when I attempt to connect, it loads for a while and then stops.  Manual configuration also fails.  I have absolutely no experience when it comes to wireless networking, so could someone help me out?

---

### Post by gli8600 on 2007-10-20
same problem here, wonder how linux wants to compete with MS with problem like this.

---

### Post by Architeuthis on 2007-10-20
There are more people with a very similar issue (like me), see this thread: [http://ubuntuforums.org/showthread.php?t=582033](http://ubuntuforums.org/showthread.php?t=582033)

---

### Post by unprinted on 2007-11-22
I don't have a problem connecting to a Linksys (albeit with a different firmware, but that shouldn't make a difference) with the same network card...

... **provided that** I change the setup of the network after each boot. What I'm currently doing is switching, each time, between DHCP and static IP. This produces a 'changing interface configuration' message in the network program and it then works. If I don't do this, although it worked last time, it doesn't work the next time.

So it looks like something isn't being properly initialised on each boot.

Yes, it worked without this in 7.04.

On the other hand, memory is telling me you had to compile the driver from source in 6.10 and there was some other problem with another version.

---

