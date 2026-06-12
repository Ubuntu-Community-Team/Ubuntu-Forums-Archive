---
title: "How to configure for non-WEP?"
date: 2007-09-06
forum: Networking &amp; Wireless
---

### Post by manicmonk on 2007-09-06
I have successfully installed my Netgear 311v3 card on Feisty. To verify, I temporarily configured my network for WEP and it works perfectly. 

Unfortunately I cannot use WEP normally because of compatibility with other network devices (I limit access by MAC address), but the GUI ONLY gives me the option of WEP (hex or ascii).

How do I configure for a non-WEP (=open) network? 

Thanks!!

---

### Post by karvec on 2007-09-06
You don't need to configure anything...  Just set wireless to roaming, and it will connect to your network automatically.  Or, just leave the WEP field blank.

Hope this solves your problem!


~~karvec

---

### Post by manicmonk on 2007-09-06
Thanks. I'd tried both roaming and a blank WEP password originally and it didn't work - that's why I experimented with turning WEP on.

I don't know what I did, but my wireless network disappeared after the last reboot - I did "modprobe ndiswrapper" again and ...bingo! Now it's working like a champ!

---

