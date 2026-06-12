---
title: "postfix unreachable from the WAN"
date: 2014-04-29
forum: Networking &amp; Wireless
---

### Post by hojjat on 2014-04-29
I setup postfix on this machine and I can connect to it locally using *telnet domain.name.com 25*. It can also successfully send out emails to the outside world. However, it cannot receive emails. I have investigated and realized that no machine from the outside can reach my machine on port 25 (telnet just times out). I also investigated and made sure that no firewall is in place, and that postfix is listening to 0.0.0.0:25 as it should. Any recommendations as to what to check next?

---

### Post by hojjat on 2014-05-06
Any ideas?

---

### Post by SeijiSensei on 2014-05-06
Your ISP may forbid servers under its Terms of Service and block inbound traffic on port 25 (and others) as a result.  Ask them.

---

