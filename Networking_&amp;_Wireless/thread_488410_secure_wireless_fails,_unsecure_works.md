---
title: "secure wireless fails, unsecure works"
date: 2007-06-30
forum: Networking &amp; Wireless
---

### Post by anagnost68 on 2007-06-30
If I disable security from my wireless router, my Netgear 311t card in Ubuntu 7.04 can communicate to the wireless router. If I enable security (WEP, 64), it cannot connect. I've tried setting the key both through the gui and by using iwconfig ath0 key <key> and it still doesn't work.

Any suggestions?

---

### Post by kevdog on 2007-06-30
To try with WEP, I would probably try first to manually edit my /etc/network/interfaces file before abandoning your attempt.  

Make sure your drivers support wep (likely they do)

---

### Post by anagnost68 on 2007-06-30
The interfaces file looks the same as my other Ubuntu machine, which works.  How do I make sure my drivers support wep?

---

### Post by anagnost68 on 2007-06-30
I changed my router to 128-bit encryption and changed my card to use the new key and it worked.

---

