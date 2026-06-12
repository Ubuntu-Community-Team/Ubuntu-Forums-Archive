---
title: "SMC wireless card (SMCWPCI-G)"
date: 2005-09-21
forum: Networking &amp; Wireless
---

### Post by .tommie on 2005-09-21
I've searched Google and noticed SMC wireless cards are kinda difficult to install for new Linux users (yeah, a newbie  \\:D/ ).

Ubuntu has been installed as OS for the family computer, but setting up the wireless card is problematic. The computer does find some wireless networks (even from the neighbourhood), but I can't connect with mine (which is using WEP 128-bit authentication).

The wireless card is an [SMCWPCI-G](http://www.smc.com/index.cfm?event=viewProduct&localeCode=EN_USA&cid=5&scid=31&pid=1478).

Does anyone have usefull information on how to setup this card?

---

### Post by .tommie on 2005-09-25
I've been experimenting for a couple of days with Ubuntu, and found a solution. I'm posting it here, because it might help other people struggling with their wireless setup.

It appears Ubuntu Breezy only supports 64-bits encryption, while I was using 128-bits encryption and WPA. I turned down encryption a nudge, and it worked.

The only thing I was worried about after simplifying encryption is security. I've decided that I'll keep this setup, but **with** an extra layer of security (namely MAC addresses filtering).

Conclusion; the SMCWPCI-G is supported out of the box by Ubuntu Breezy, but you have to run 64-bits encryption for now.

---

### Post by unrealdark on 2005-12-29
What Drivers are you using??? 
Can anyone tell me if this chipset is atheros?

---

### Post by .tommie on 2006-06-17
A late reply... ;)

All I can tell is that Breezy and Dapper support it natively!

---

### Post by amunimanghi on 2006-06-23
when you plugged it in, what did you do. I have the exact same one and im trying to get it to work. I have it plugged in and in my **Networking** application, i have it enabled and set as the default (ath0). I haven't restarted yet. I have the eth0 enabled also. Should I disable eth0 and restart?

---

### Post by .tommie on 2006-06-23
I've installed Network Manager, following [this]("https://help.ubuntu.com/community/WifiDocs/NetworkManager") guide. WPA support is included and easy to setup.

That's it. :)

---

