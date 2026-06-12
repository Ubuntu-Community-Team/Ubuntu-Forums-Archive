---
title: "Help! Serious connection problems"
date: 2008-09-18
forum: Networking &amp; Wireless
---

### Post by ZackGRR on 2008-09-18
Hi. I am completely new to Ubuntu and open source. I just got a new laptop (Asus M51V series) and decided I would try Ubuntu whilst keeping Windows. One wasted weekend later I ended up scrapping Windows (because I think I screwed it up) and keeping just Ubuntu. But it is still giving me many headaches and wasting a lot of time. And I am a complete amatuer. So please help!

Sometimes it tells me I am connected to a wired network when I'm not (including when I'm actually connected to a wired network, it just doesn't work) and now I'm trying to connect to a wireless network, and I don't think my wireless driver or whatever is even recognised, as there's no wireless option whatsoever, even though I'm simply trying to connect to a unsecured network. Help please!

---

### Post by Iowan on 2008-09-18
As far as the wired network... If you are set to get IP address via DHCP, and that attempt fails, a program **avahi** assigns a network address in the 169.x.x.x range.  This is the **local zeroconf** option, but sometimes seems to spring into action anyway. Run **ifconfig** to see what (if any) address you're getting.

---

### Post by ZackGRR on 2008-09-20
Thanks for that - I'll try it if I have problems again. It's intermittent problems with wired networks.

Anyone able to help me with the wireless? Would 802.11abgn + BT have anything to do with the type of wireless driver it is? (Sorry, I'm way out of my depth here)...

---

### Post by pyth3n on 2008-10-06
Bump.

I seem to have this problem also. Any help would be much appreciated.

---

### Post by Jonno_FTW on 2008-10-18
> **pyth3n said:**
> Bump.

I seem to have this problem also. Any help would be much appreciated.

Me too, the wireless internet doesn't work, but bluetooth does though. AND there is also no sound.

---

