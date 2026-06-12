---
title: "Restrict windows network shares"
date: 2008-06-13
forum: Networking &amp; Wireless
---

### Post by paquinhq on 2008-06-13
Hi everyone!

I'm trying to block windows network shares in hardy. I've tried to uninstall all samba related stuff but synaptics requests gnome removal if i do that. Is there a way to disable the access to windows shares on the network from gconf-editor or another restriction managememt application?

Thanks in advance for your help.

---

### Post by kidders on 2008-06-15
Hi there,

It's not clear from your post whether you're interested in blocking access to remote shares, or preventing users from exposing local ones to your network. Short of recompiling Gnome, my best suggestion is to block Windows networking-related traffic with iptables. That way, it won't matter what's enabled in Gnome's UI, because none of the Windows networking features will get access to the network.

---

