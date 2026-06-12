---
title: "Remote Desktop"
date: 2009-07-27
forum: New to Ubuntu
---

### Post by rvgsd on 2009-07-27
Hi, 
I am using Ubuntu 8.04 and my friend is using XP (Professional).
We are not in a LAN.
Is it possible for me to use remote desktop just over internet? how?

Thanks for help.

---

### Post by bodhi.zazen on 2009-07-27
Yes. You need to forward the port (5900) from the router. Take care, VNC is probably the most often cracked server on these forums.

---

### Post by rvgsd on 2009-07-27
Thanks for informing. Do I need to forward the port or does he need to??
Please clarify...this can be done from the router settings right??
Thanks again!

---

### Post by XCan on 2009-07-27
Do you want to access your friend's computer or vice versa? If you want to access your friend's he will need to forward port **3389**, which is the port Windows RDP uses.

If your friend want to access your computer then it is as bodhi says, that you need to forward port 5900 since VNC is the default protocol Ubuntu uses.

As you see, windows remote desktop and ubuntu's 'remote desktop' uses different protocols.

---

### Post by bodhi.zazen on 2009-07-27
he needs to forward a port (assuming his is the server and you are the client connecting to his computer).

---

### Post by rvgsd on 2009-07-28
port forwarding.. got it! thanks guys for help!

---

