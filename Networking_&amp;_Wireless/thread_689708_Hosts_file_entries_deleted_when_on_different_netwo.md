---
title: "Hosts file entries deleted when on different network?"
date: 2008-02-06
forum: Networking &amp; Wireless
---

### Post by Alhazred on 2008-02-06
Hi guys.

The scenario below may seem a little strange, but what the heck.

I have a cheap old Dell laptop running Dapper, which I use for most everyday chores. I usually connect wirelessly when at home. I also take it with me once in a while when I am travelling, and connect to various public wifi hotspots.

My /etc/hosts file contains a number of entries specific to my home network to aid with name resolution. I notice that after I connect to an outside network, these entries are deleted. That is to say, when I am back on my home network, and think to open my hosts file, they are gone.

I keep a backup of the file, so this is not really that much of a pain. But it seems like such an odd problem that I would like to find out what is going on, if only to reassure myself that I am not hallucinating.

Mick

---

### Post by jetsam on 2008-02-10
This [thread]("http://ubuntuforums.org/showthread.php?t=554771") has  a possible cause (network manager), and a suggested fix.

---

