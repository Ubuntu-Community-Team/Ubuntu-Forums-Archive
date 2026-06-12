---
title: "Not use wireless, can I drop networkmanager"
date: 2008-07-07
forum: Networking &amp; Wireless
---

### Post by lil_elvis2000 on 2008-07-07
I am using 8.04 with kernel 2.6.24-19(I think). I am not using any wireless networks nore DHCP - its all static IPs. Do I need NetworkManager?
NetworkManager really annoys me. It spits out messages about my KVM, when I switch away and when I switch back. It even spits out HAL messages. I'd rather these messages didn't appear on my console. They didn't before..I think I may have upgraded a component without knowing.
After some time the USB ports die (after a few hours) and there are error messages on the screen. I think these are all related to NetworkManager.
I'd prefer not to use it if I can.

Can anyone advise me?

---

### Post by pytheas22 on 2008-07-07
Yeah, I'm not a big fan of Network Manager either.  I wish Ubuntu would use something like wicd by default.

Anyway, I don't see any problem with uninstalling NM.  As far as I know, the only thing that it does for wired connections is get an IP over dhcp when it detects a cable plugged in.  If your IPs are all static, then I don't think NM is doing anything for you.

---

