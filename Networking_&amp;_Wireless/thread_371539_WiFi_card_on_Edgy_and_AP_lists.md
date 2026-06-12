---
title: "WiFi card on Edgy and AP lists"
date: 2007-02-27
forum: Networking &amp; Wireless
---

### Post by txapelgorri on 2007-02-27
Hi there:

Few weeks ago I decided to migrate from Dapper to Edgy on my laptop, and I realize that my WiFi PCMCIA card, refuses to show me the list of the APs near me. Dapper used to show them with no problem at all.
The card is a 54Mbs Conceptronic one, which loads atheros module. It works well with Edgy, but I must to scan the air on console: no problem for me, but yes for another people that uses the same laptop. Did you know why I can't see that list?

Cheers, Ibon.

---

### Post by spd106 on 2007-02-27
Hi, 

Yes, this is a known issue. The bug has been fixed upstream, but looks like it is unlikely to be backported to edgy. You can see the bug report here [https://launchpad.net/ubuntu/+source/gnome-system-tools/+bug/59159](https://launchpad.net/ubuntu/+source/gnome-system-tools/+bug/59159)

---

### Post by txapelgorri on 2007-03-01
Hi:

Thanks. I've read all the thread, and I hope the team to backport to Edgy.

Cheers, txapelgorri.

---

