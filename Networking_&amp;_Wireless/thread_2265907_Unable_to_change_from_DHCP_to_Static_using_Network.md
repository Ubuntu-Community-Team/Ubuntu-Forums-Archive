---
title: "Unable to change from DHCP to Static using Network Manager in Gnome 3.14"
date: 2015-02-18
forum: Networking &amp; Wireless
---

### Post by EmyrB on 2015-02-18
Hi Guys,

Installed Ubuntu Gnome 15.04 today to give it a whirl. So far everything is ok, except networking. Currently my IP address is set to dhcp, but how on earth do I change it to static. If I use the network in settings, I just get a screen showing my network speed and a toggle button to say it's active. I can't add a new wired profile and nothing else is clickable.

Any ideas?

Cheers

EmyrB

EDIT: Figured out how to do it, but it's a bit of a cludge. There is a program called Network Connections (nm-conection-editor) but if you run it, it doesn't show you any info. If you try and add a new connection, then it gives you a warning about unknown username when you try to save it. So, if I run nm-connection-editor as root (sudo) the information is displayed and I can change the settings. As I said, it's a bit of a cludge, not sure if this is a bug with Gnome or Ubuntu as 15.04 is still in Beta.

---

### Post by TheFu on 2015-02-18
15.xx is early beta software, right? 
Issues for that OS should be posted to the Ubuntu+1 forum.

---

