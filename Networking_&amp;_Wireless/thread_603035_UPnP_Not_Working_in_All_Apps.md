---
title: "UPnP Not Working in All Apps"
date: 2007-11-04
forum: Networking &amp; Wireless
---

### Post by Computer Guru on 2007-11-04
Hi,

I can't get UPnP to work in any of my apps since switching to Gutsy (clean install).

Connecting to the modem directly works, and using a different OS (XP or Feisty) also works from behind my UPnP-enabled router.

Any idea what might be stopping UPnP from running on Gutsy? Running as sudo does not help. Also tried removing apparmor, made no difference.

Any help would be appreciated.

Thanks!

---

### Post by puccaso on 2007-11-04
try installing azerues, see if it works on that

---

### Post by Computer Guru on 2007-11-04
No, it doesn't.

I've tried it on Azureus, uTorrent, Deluge, FileZilla, my own C#/Mono server, and a bunch of other stuff. Makes no sense :S

---

### Post by puccaso on 2007-11-04
try seeing if u have iptables installed. its a firewall app.. it may be blocking some ports that are required for upnp to work.
also, although u said ur router is upnp complient, maybe u wanna try another pc with some upnp software to see if it actually works
you want to isolate the problem to a certain location, ur router, ur system or the software..

---

### Post by Computer Guru on 2007-11-04
OK, this is weird.

It seems to be not so much a UPnP issue as it as a NAT traversal issue.

Even after setting up port-forwarding (manually choosing select ports) they're not seen across my router.

Intra-network they're seen just fine, but from outside the packets aren't reaching via a port-forward, even if I set my IP as the DMZ! (which is weird, because then all ports should be open no matter what).

DMZ, UPnP, and port forwarding work with other OSes.

I'm using dd-wrt on a hacked WRT54G v5. Haven't ever had problems with it.

---

### Post by puccaso on 2007-11-04
u mean on other os's on ur ip?
or other os's on the network?

---

### Post by Computer Guru on 2007-11-04
lol, other OSes on the same PC :)

---

### Post by puccaso on 2007-11-04
ok
then its ur ubuntu setup.

remove iptables and see how it goes..

---

