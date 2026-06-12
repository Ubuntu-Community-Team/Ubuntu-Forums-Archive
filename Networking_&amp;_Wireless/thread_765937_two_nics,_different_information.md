---
title: "two nics, different information"
date: 2008-04-24
forum: Networking &amp; Wireless
---

### Post by ElJefeRocks on 2008-04-24
Hello,

I have a server set up that streams my music library and downloads torrents via torrentflux.  I have two nics in the machine, and would like to dedicate one nic to each of the two processes.  I haven't any idea of how to search it and a few minutes in google really came up with nothing except that I might not be able to do it as the two would still be on the same netmask (maybe?).

So, really all I want is
eth0: all internet except ports for torrents
eth1: only torrent ports (50 of them)

Any ideas on how this would be accomplished?


Server has 6.06.2 with the linux-k7-smp kernel.  I have access via ssh and it also has webmin if that helps anything.

Thanks!

---

### Post by ElJefeRocks on 2008-04-26
bump... I feel this has been pushed to the bottom by gutsy problems...

---

