---
title: "LAN crashes"
date: 2005-08-19
forum: Networking &amp; Wireless
---

### Post by [pl]ice on 2005-08-19
hi,
i got running lan on p2p with xp. Problem arises when i mount the remote share, and if later the other pc is switched off.
   I cannot umount my share folder , (device busy) i cannot get into it... i can't use ifconfig etc. commands...
  the KDE 'process' manager tool shows 8888 everywhere (in ram etc) displays no processes, yet top/ other show it's ok ...
  i read that adding to mount options: _netdev should resolve it, but i haven't add it this time...

how to resolve this problem?

is there a way to 'kill' mount folder, while it tries constantly connect to other pc?
  i know i created 'zombie' which tries to connect to other box, but not sure how to fix it :)
thanks.

---

### Post by nad on 2005-08-20
Try the -l (lazy) or -f (force) switches to the umount command.

---

