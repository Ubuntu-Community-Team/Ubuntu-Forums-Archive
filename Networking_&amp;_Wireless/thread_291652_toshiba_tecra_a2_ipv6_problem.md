---
title: "toshiba tecra a2 ipv6 problem"
date: 2006-11-02
forum: Networking &amp; Wireless
---

### Post by Nikusan on 2006-11-02
Hi all,

just installed edgy on the above notebook and I'm having (what I think is) ipv6 problems. I turned it off in firefox's about:config and I can now browse the web. Command line tools like ping and such work but no GUI apps can connect to the net (like synaptic and gaim for example). I've turned off ipv6 with the 3 lines added to /etc/modprobe.d/aliases and rebooted. The strange thing is this has not fixed my problem.

Any advice?
ta

EDIT: when doing an apt-get update it says "connecting to archive.ubuntu.com (1.0.0.0)". This is obviously wrong.

EDIT: It turns out that the router was giving crappy DNS info (see above...) so we just use the ISP's DNS servers explicitly and it all works fine. It's odd that windows machines aren't affected though.

---

