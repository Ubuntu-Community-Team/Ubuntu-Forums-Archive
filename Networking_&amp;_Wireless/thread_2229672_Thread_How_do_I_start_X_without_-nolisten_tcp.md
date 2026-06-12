---
title: "Thread: How do I start X without -nolisten tcp?"
date: 2014-06-14
forum: Networking &amp; Wireless
---

### Post by Graeme_V on 2014-06-14
This thread got closed , so I could not add to it. (previous posts were very useful)

... this seems to be the main place you end up when researching how to get XDMCP working. So to add my 2 cents:

On recent ubuntu:

edit /etc/lightdm/lightdm.com  (read the file /usr/share/doc/lightdm for background)

xserver-allow-tcp=true
[xdmcp]
enabled=true
port=177

then edit /etc/x11/xinit/xserver
remove the -nolisten tcp for the command

... on a Debian box (running gnome3) [ yes I know this is ubuntu ... but doing xdmcp , presumably  there are other machines involved :-) ]

same edit to /etc/x11/xinit/xserver but:

edit /etc/gdm/daemon.conf

[security]
DisallowTCP=false

[xdmcp]
Enable=true
Port=177

(case is important)

---

