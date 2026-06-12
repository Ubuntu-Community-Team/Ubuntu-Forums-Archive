---
title: "btdownloadheadless and firestarter"
date: 2006-08-29
forum: Networking &amp; Wireless
---

### Post by bPawn on 2006-08-29
so... I have installed the firestarter firewall and allowed for in/outbound
the ports: 6881-6889

To test the configuration I run:
screen btdownloadheadless ubuntu-6.06.1-alternate-i386.iso.torrent --minport 6881 --maxport 6889 --spew 1

The result:
ERROR: Problem connecting to tracker - <urlopen error (111, 'Connection refused')>

I allowed the outbound connections for port 6969 (Gatecrasher) and it worked.
However for all the other torrents I have the same problem.

Is there a way to specify which port is used for outbound connection. Any other solution?

---

### Post by bPawn on 2006-08-30
Anybody?

---

### Post by tturrisi on 2006-08-30
get rid of firestarter, you don't need it!

---

