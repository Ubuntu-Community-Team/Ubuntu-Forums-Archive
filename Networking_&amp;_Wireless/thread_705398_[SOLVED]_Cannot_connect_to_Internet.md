---
title: "[SOLVED] Cannot connect to Internet"
date: 2008-02-23
forum: Networking &amp; Wireless
---

### Post by sfox on 2008-02-23
I just installed Ubuntu 7.10 on my T43 thinkpad with Intel 220BG(Wireless) and Broadcom NetXtreme Gigabit Ethernet. I am doing well with internet at company through Cisco switch/router. But it is not working through TP-Link(WR340G) adsl router at home. There is a very strange thing, I can visit [www.google.cn](www.google.cn), but cannot visit [www.google.com(I](www.google.com(I) can ping [www.google.com](www.google.com)) under ubuntu 7.10.  I am sure I get right IP address, DNS and firefox config, I also try 1.disable IPv6 and add a backlist into config 2.Modify the MTU to 1452. It is still not work properly.

Does anyone tell me next step to make my internet work?

---

### Post by mrsteveman1 on 2008-02-23
If you can visit google.cn in a browser, and can ping google.com, the only difference is that perhaps communications with google.com on port 80 are being blocked. There is no other real reason for ping to work but not http.

---

### Post by sfox on 2008-02-23
I do well under windows XP with same configuration. Another example, I can visit [www.mozilla.org](www.mozilla.org) or [www.firefox.com](www.firefox.com), but can not visit [www.ubuntu.com(I](www.ubuntu.com(I) can ping [www.ubuntu.com](www.ubuntu.com)) by firefox.   I have tried as many as I can find from web, no luck.

---

### Post by sfox on 2008-02-23
Just FYI, I installed Fedora 8 on my T43, it is working well. So I think maybe something I miss under Ubuntu 7.10.

---

### Post by mrsteveman1 on 2008-02-23
Weird, i suppose perhaps the DNS could be acting funny, have you tried resolving google.com directly and using its IP address in a browser instead of its domain name?

---

### Post by sfox on 2008-02-23
Yes, I tried. The problem is remain.

---

### Post by sfox on 2008-02-24
I change my adsl router to another model, the problem is solved. So I think myabe there is a bug in the adsl router firmware.

---

