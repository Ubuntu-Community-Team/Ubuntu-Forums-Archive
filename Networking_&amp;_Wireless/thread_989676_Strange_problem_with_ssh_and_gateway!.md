---
title: "Strange problem with ssh and gateway!?"
date: 2008-11-21
forum: Networking &amp; Wireless
---

### Post by rhcm123 on 2008-11-21
I have my servers (some ubuntu based, others windoz). Now, for security reasons, i dropped in a firestarter gateway between the internet and the windows machines. I am able to ping out, but i am not able to ping in to the server! I can also not ssh or telnet, etc. I have to ssh to the firestarter machine, then ssh to the server. This is a problem because now my computers can't get to the samba shares.

I have everything open but I still cannot connect. :( anybody know why?

---

### Post by superprash2003 on 2008-11-22
you would need to NAT for this [http://www.revsys.com/writings/quicktips/nat.html](http://www.revsys.com/writings/quicktips/nat.html)

---

### Post by rhcm123 on 2008-11-22
> **superprash2003 said:**
> you would need to NAT for this [http://www.revsys.com/writings/quicktips/nat.html](http://www.revsys.com/writings/quicktips/nat.html)

that does outbound traffic- which already works. I need inbound traffic, so that I can ping things behind the gateway.

---

