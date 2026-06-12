---
title: "ipv4 vs ipv6"
date: 2007-08-21
forum: Networking &amp; Wireless
---

### Post by newbieal on 2007-08-21
Is there a way to force my network to autoconfigure with ipv4? Alternately, how can I change my network from ipv6 to ipv4? Right now it always comes up in ipv6.

I have a winxp internal network using an ubuntu-fiesty PC for the dhcp-server, samba file share and ICS router. I still can't get the ICS part to work, but when I can access the internal nework, it works great. I just can't get to it consistently.

I would appreciate any susggestions.

---

### Post by ajgreeny on 2007-08-21
You can do it in firefox by typing about:config in the address bar, ipv6 in the filter box and changing network.dns.disableIPv6 to true.
To do it system-wide edit /etc/modprobe.d/aliases with:-
[FONT=courier new]gksudo gedit /etc/modprobe.d/aliases
Look for the line
[/FONT][COLOR=#CC0000]**[COLOR=Black]alias net-pf-10 ipv6[/COLOR]**
[COLOR=Black]and change it to[/COLOR]
[/COLOR][COLOR=#006600]**[COLOR=Black]alias net-pf-10 off #ipv6[/COLOR]**

[COLOR=Black]Now edit /etc/hosts and comment out all lines to do with ipv6, save it and reboot.[/COLOR]
[/COLOR]

---

### Post by newbieal on 2007-08-22
I followed your instructions, and now have my network back. Great!

Thanks for your input

---

