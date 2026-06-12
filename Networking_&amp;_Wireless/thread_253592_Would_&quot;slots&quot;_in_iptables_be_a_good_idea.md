---
title: "Would &quot;slots&quot; in iptables be a good idea?"
date: 2006-09-08
forum: Networking &amp; Wireless
---

### Post by pelle.k on 2006-09-08
Hi all. As always i'm thinking of possible solutions to problems which are nagging me in linux.
If only one application make changes to iptables, all is fine, but if more than one application wan't access, there will be a mess. I can't think of one good reason why iptables couldn't have "slots" and report which of them is in use, so applications can choose a free one.
One scenario is the conflict between a popular GUI frontend like firestarter, and filtering applications like peerguardian and moblock. That doesn't work. One could patch firestarter to make it comliant with the rules needed to make peerguardian/moblock to work, but that would be a fix only relevant to those applications.
Presently, you have to write the rules by hand to make it work, but if "slots" were used, we wouldn't have these problems. 
Ideas, comments?

---

### Post by tbonius on 2006-09-08
Are you referring to remote application dynamically calling a port range to open as requested?  uPnP functionality natively in IPtables would be nice.  Check out UPnPd:

[http://upnp.sourceforge.net/](http://upnp.sourceforge.net/)

[http://linux-igd.sourceforge.net/documentation.php](http://linux-igd.sourceforge.net/documentation.php)

Theres a WIKI on doing it in Gentoo.. I think I'll give a stab at making it run in Ubuntu tonight:

[http://gentoo-wiki.com/HOWTO_Setup_UPnP_with_IPTables](http://gentoo-wiki.com/HOWTO_Setup_UPnP_with_IPTables)

T

---

