---
title: "networkmanager-pptp support for logon domains?"
date: 2007-03-31
forum: Networking &amp; Wireless
---

### Post by ReinesU on 2007-03-31
I've been trying to connect to a VPN using the pptp plugin for networkmanager (nm-applet), but as far as I can see there is nowhere to specify a logon domain, does this mean it doesn't support them or is there maybe a custom option to specify one?

The only related thread about this that I could find was [this one](http://ubuntuforums.org/showthread.php?t=289769&highlight=networkmanager+vpn), which is no real help.

Thanks if anyone has any suggestions :confused:

PS. Im running Ubuntu Edgy (kernel: 2.6.17-11-generic)

PPS. domain//username and username@domain don't work (they were just guesses anyway)

---

### Post by WinterHico on 2007-05-23
I am having the same problem in Feisty.  I tried to add "domain <domain>" to the PPP options of the VPN configuration in networkmanager.  It appears as though there is a list of allowed options and "Currently there are no options on the list."  Does that mean we cannot add any options.

Also, when connecting to this VPN through Windows, I need to setup a "Preferred DNS" server. I'm not sure how to do that in the VPN configuration with networkmanager.  I believe I should be able to add PPP option "nameserver xxx.xxx.xxx.xxx", but again, I don't seem to be able to add any PPP options.

---

