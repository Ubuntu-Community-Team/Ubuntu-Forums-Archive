---
title: "Can't set WEP on boot time with ipw2200"
date: 2005-04-10
forum: Networking &amp; Wireless
---

### Post by Vide on 2005-04-10
Hello everyone

I'm running Hoary 5.04 on a HP Pavillion ze4900. Everything works smoothly, my wifi card is detected since the very first install process but I have a little problem with it anyway.

I want to use it in ad-hoc mode, not in managed, so I've modified /etc/network/interface adding "wireless-mode ad-hoc" in the eth1 section. This work fine. But if I leave in the sam file the setting "wireless-key mykey" on boot time the ipw2200 module complains about failing sending TX_POWER, and while the IF is up, the link isn't, until I manually launch "iwconfig eth1 enc open s:mykey" (since my key is textual). After doing this, it works smoothly and I can ping the other host and navigate through it the internet. How can I resolve it? The problem is that every time the IF go down (for example, hibernating) I have to repeat this process, and on every reboot too, and it's very frustrating.

---

