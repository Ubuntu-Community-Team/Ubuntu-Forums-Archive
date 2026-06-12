---
title: "Cannot get 'fanatic' to see LXD installed via Ubuntu's 'snap'"
date: 2024-11-20
forum: Networking &amp; Wireless
---

### Post by g01d10x on 2024-11-20
Hello Forums :)

I have a couple of serves with LXD installed via the snap, and just read about and tried to set up a fan network using fanatic.

This is what I get:

[COLOR=#000000][FONT=Menlo][COLOR=#2fb41d]**me@server1**[/COLOR]:[COLOR=#400bd9]**/etc/network**[/COLOR]$ fanatic enable-lxd[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Reconfigure fan underlay (hit return to accept, or specify alternative) [10.2.0.0/16]: [/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Reconfigure fan overlay (hit return to accept, or specify alternative) [250.0.0.0/8]: [/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]LXD not installed, unable to configure[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo][COLOR=#2fb41d]**me@server1**[/COLOR]:[COLOR=#400bd9]**/etc/network**[/COLOR]$ [/FONT][/COLOR][COLOR=#000000][FONT=Menlo]which lxd[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]/snap/bin/lxd[/FONT][/COLOR]

I tried looking around for snap networking fan lxc lxd ubuntu in various combinations, but couldn't find any guidance. Any help would be appreciated :)

---

