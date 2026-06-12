---
title: "Via-Rhine Broken Bios (No internet)"
date: 2008-10-15
forum: Networking &amp; Wireless
---

### Post by alan888 on 2008-10-15
Hi:

I recently installed ubuntu 8.04 in my "pc-router", but my network interfaces is not recognized. I have 2 interfaces, but the LAN interface work fine. My internet modem only accept the MAC of my "not-recognized" interface.

I look for it in lspci and it appear. Later, I used:
```

sudo dmesg | grep rhine 
```
And I have:
```

       [] via_rhine: Broken BIOS detected, avoid_D3 enable.
       [] via_rhine: Reset not complete yet. Trying harder.
       [] via_rhine: probe of 000:00:06.0 failed with error -5

```

I probe the ethernet card in other PC (winxp) and it work fine.
I have been looking for something on internet, but nothing appear or always is some error in /etc/network/interface file, it's not the case.

What can I do?
Can you help me, please? Tanks

---

