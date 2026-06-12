---
title: "Wireless sometimes lost are Resume from Standby"
date: 2007-08-21
forum: Networking &amp; Wireless
---

### Post by technikalKP on 2007-08-21
I have a Dell inspiron 700m with a Intel 2200 wireless card running Ubuntu 7.04.  Occasionally and seemingly randomly, when returning from Standby, my wireless card 'disappears'.  This happens using both gnome-network-manager and wicd.  The utilities can no longer reconnect automatically (I'm in the same area using the same network when coming back from standby) and trying to force a reconnect doesn't work either.  It seems like maybe the card is not waking up or something.  90+% of the time it works perfectly, but when it doesn't I have to reboot to regain connectivity.

I'm really not sure where to begin troubleshooting.  Any pointers?  How do I tell if I'm dealing with a card not waking up or some software issue? (the 'wireless' indicator light on the 700m doesn't work with Ubuntu)

Is there the equivalent of the 'Repair' option in XP's wireless manager in Ubuntu?

Thanks!

---

### Post by scrooge_74 on 2007-08-21
when this happens, open a terminal and type ifconfig

if the card shows up, maybe do sudo ifdown {ID of card} 

then sudo ifup {ID of card}

maybe it will reenable it in the network manager

---

