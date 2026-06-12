---
title: "My internet won't connect"
date: 2008-06-20
forum: Networking &amp; Wireless
---

### Post by StarWOLF100 on 2008-06-20
My Scientific Atlanta Cable Modem won't connect about the 9 out of 10 times I restart my computer. Is there anyway to fix this problem? I tried everything I could with no result.

---

### Post by nixscripter on 2008-06-20
1. When it doesn't work, is there anything in /var/log/messages that stands out?
2. What driver does it use, and is that driver being loaded every time? It should be somewhere in /etc/modules or /etc/modules.d
3. Is it a protocol problem between the modem and the server, or the computer and the modem?

I'm not sure about this kind of modem, but usually, there are a few usual things to check.

---

### Post by adam s.. on 2008-06-22
I have the same problem on Xubuntu.
the icon shows that the computer is connected, but the computer doesn't connect.

---

