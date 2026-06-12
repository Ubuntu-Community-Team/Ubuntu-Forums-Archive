---
title: "[SOLVED] Close a specific port!"
date: 2008-02-18
forum: Networking &amp; Wireless
---

### Post by brett611 on 2008-02-18
Hi all,
I used Azureus for the first time to try it out.  I started downloading something, it said it'd take 2 days to finish so I cancelled and deleted the file and the torrent.

Now Firestarter is blocking about 5-10 connection attempts on port 10128, which is the port Azureus was config'd to use. Firestarter is using 60% of my CPU according to system monitor...

How do I stop this?  I'm not certain what exactly this is but I'm figuring since the Firestarter icon is flashing red, its bad.  I've uninstalled Azureus.

Thanks!

---

### Post by SpaceTeddy on 2008-02-18
> sudo iptables -A INPUT -p tcp --dport 10128 -j DROP

this adds a drop rule to the ip filter which drops all packets with protocoll tcp send to you on port  10128

this rule will need to be reloaded every time you reboot your pc until your ip changes (if you have dynamic IP). makes me wonder what firestarter does...

---

