---
title: "firewall options"
date: 2016-02-15
forum: Networking &amp; Wireless
---

### Post by balmof_gilead on 2016-02-15
i have had windows for my OS pretty much forever the best firewall i have ever found for it was "outpost" this let me see exactly the full details of everything trying to communicate with my pc through the Ethernet, exactly what website and the company behind it, every  program or app, and full control over all of it  i am looking for something i can run in ubuntu, or mint, with the same, or better results / control this is the best info i can find  [http://distrowatch.com/search.php?ostype=Linux&category=Firewall&origin=All&basedon=All&notbasedon=None&desktop=All&architecture=All&package=All&rolling=All&isosize=All&netinstall=All&status=Active](http://distrowatch.com/search.php?ostype=Linux&category=Firewall&origin=All&basedon=All&notbasedon=None&desktop=All&architecture=All&package=All&rolling=All&isosize=All&netinstall=All&status=Active)  problem is, these all seem to be like an OS that would control a router or server, not run inside of an OS to control the networking of it any advice would greatly be appreciated

---

### Post by blueridgedog on 2016-02-15
Iptables is the build in firewall.  There are a few graphical interfaces for it, firestarter is one:

[http://www.tecmint.com/firestarter-a-high-level-graphical-interface-iptables-firewall-for-linux-systems/](http://www.tecmint.com/firestarter-a-high-level-graphical-interface-iptables-firewall-for-linux-systems/)

---

### Post by B._Bishop on 2016-02-20
Thank you Blueridgedog!

The page instructed (yes im a noob lol) sudo apt-get update n install firestarter, i get the error package not found...
Any other way to get it, or an alternative to firestarter?

thanks in advance

---

### Post by sammiev on 2016-02-20
[GUFW]("https://help.ubuntu.com/community/Gufw") is in the software center.

---

### Post by B._Bishop on 2016-02-20
Thank you!!

---

### Post by B._Bishop on 2016-02-20
Thank you!!! Works like a charm!

---

### Post by sofasurfer on 2016-03-27
I just tried Firestarter. I have incoming set to "reject" (also tried "deny") and I get no notification when a site loads. Shouldn't I get asked for confirmation?

---

