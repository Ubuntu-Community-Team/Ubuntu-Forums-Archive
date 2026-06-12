---
title: "Modem init in Hoary?"
date: 2005-06-29
forum: Networking &amp; Wireless
---

### Post by forstfed on 2005-06-29
Can someone PLEASE tell me where I can enter a modem init string to get my ext USR modem to connect at better speeds?  I have tried manually entering in any and every script file I could find and still not connecting.  One would think that the Network modem utility would would have an area to enter init strings, sorta like kppp does?

Thanks,

Ed

---

### Post by alastair on 2005-06-29
This stuff is arcane knowledge .. and I am not a high-degree initiate.

But it might be something in a "chat" script under /etc/ppp/peers/.

See: man chat

For the brave.

---

### Post by forstfed on 2005-07-05
ok, I found where to do the init script, I think i had to modify the pap and/or the ppp0 script (modifying scripts, talk about yesterdays newspaper).  Now that i get the 2 "bongs" indicating a 56k handshake with usr modems, I get immediately disconnected from my ISP. Any ideas anyone?

Ed

---

### Post by alastair on 2005-07-05
Logs are always the best and first place to check : /var/log/syslog

You can also add "debug" to a pppd call, and "-v" to any chat program used.

---

