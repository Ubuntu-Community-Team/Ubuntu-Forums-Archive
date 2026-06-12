---
title: "/etc/network/interfaces was overwrote again and again!Plz help!"
date: 2008-01-23
forum: Networking &amp; Wireless
---

### Post by lemonicetea on 2008-01-23
Hi, I followed the sticky threads by wieman01. However, the modified /etc/network/interfaces file will be overwirte by the origin one from time to time. How can I solve that? Thanks a lot.

---

### Post by wieman01 on 2008-01-24
What's happening there? Will be overwritten? That's impossible.

If it happens nonetheless, you could do this to revoke write rights:
> sudo chmod 555 /etc/network/interfaces
Please restart the PC and let me know if that works for you.

_**EDIT:**_
Reference: [http://www.ss64.com/bash/chmod.html]("http://www.ss64.com/bash/chmod.html")

---

### Post by lemonicetea on 2008-01-24
Thank you very much for your reply..I will try it and let you know the result.
By the way, Is there anyway that I can add two wireless configuration and It will switch between automatically? Then I can use wireless at both campus and home without any trouble. Thanks a lot.

---

### Post by wieman01 on 2008-01-24
You would have to install Network Manager. Have you tried it before?

---

### Post by lemonicetea on 2008-01-25
Wieman01, Thank you soooooooo much... Finally got my wireless working under WPA2.

---

