---
title: "Realtek RTL8111 ethernet no connectivity"
date: 2015-11-30
forum: Networking &amp; Wireless
---

### Post by dh1989 on 2015-11-30
I'm running Ubuntu 14.04 and attempting to use a Realtek RTL8111 PCI-express card. The card appears to be recognized in lspci and nm-tool, however it will not connect. It attempts to connect, disconnects, then attempts again (repeat xforever). I am currently using a wireless USB dongle for internet access. I connected my ethernet cable to my laptop and it works fine, so I have ruled out router and cable issues.

I ran the script in the forum sticky for the network debugging outputs. Here are the results:
[http://pastebin.ubuntu.com/13591121/](http://pastebin.ubuntu.com/13591121/)

I have tried blacklisting the r8169 driver to force r8168 to load. No change. I then tried downloading and installing the latest Realtek driver from the Realtek website. No change.

If I cannot successfully get this card to work I will need a suggestion as to a card that will work and is Ubuntu supported. I really need to get ethernet working on my system.

Much thanks.

---

### Post by dh1989 on 2015-12-01
If it means anything, the connection came up when I turned my PC on today. It worked fine for a few hours. I rebooted and it cannot connect once again.

---

