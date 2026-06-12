---
title: "Cannot connect to network"
date: 2007-12-15
forum: Networking &amp; Wireless
---

### Post by ihatethatguy on 2007-12-15
I spent the last hour or so looking for what i was doing wrong here but came up short.....


Ive been using the 7.10 release for about two weeks now and decided that i was going to replace windows on my internal server since i no longer have a way to remote admin it since ive gone over to linux 100%.  My intentions were to install krdc and use that to mange it from te bedroom computer.  However, i cannot see the network and neither machine sees that the other exist.  They are both able to ping each other, but krdc will not connect.  Firewalls on both are disabled, but it is behind a smoothwall machine, but i do not think that would make a lot of difference.

I am quite able to connect to windows shares via samba, internet works fine on both, so the card is functioning.  Any help on this would be greatly appreciated.

---

### Post by ubutufan on 2007-12-17
Krdc is a remote desktop connection program.
You need to set up your router by opening up a port so that the client can access the server. In windows terminology this port is 3389
In ubuntu you go to system>preferences>remote desktop and you allow the server to accept remote connections via the vnc connection.

---

### Post by ihatethatguy on 2007-12-18
There is no router involved anywhere in this process, smoothwall is acting as a firewall between the outside and my internal network, and as a dhcp server, it does not interact with the network computers in the manner of a router.  I will try to use that port that you mentioned though to tunnel through the firewall.  It has been quite difficult to find information that states exactly which ports are used by which programs.  I think that i have everything sorted except for being able to use krdc and networking through the firewall,

Anything related to netbios, nis, or samba/smb is enabled...thus far i have been able to begin a krcd session to  the remote with the firewall on local machine, as well as maintain, with both firewalls on, as well as maintain, but not initiate a networking session with both firewalls on.

---

