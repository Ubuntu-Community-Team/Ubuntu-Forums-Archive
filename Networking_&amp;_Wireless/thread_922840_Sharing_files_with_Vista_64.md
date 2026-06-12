---
title: "Sharing files with Vista 64"
date: 2008-09-17
forum: Networking &amp; Wireless
---

### Post by ubockto on 2008-09-17
Having solved this problem with XP, I am still having problems with vista-64, flavour, Ultimate

I watched on youtube how to do it with XP, and thinking that it would be the same, it is still annoying that I couldn't do likewise with Vista

---

### Post by ubockto on 2008-09-18
*bump*

---

### Post by amgat on 2008-09-18
easy. Use Samba:
[http://www.go2linux.org/how-to-install-samba-on-linux-with-swat](http://www.go2linux.org/how-to-install-samba-on-linux-with-swat)

---

### Post by amgat on 2008-09-18
You could also try this approach:

1. Go to "Places", then click "Connect to a Server"
2. Change the publicftp to "windows share"
3. Put in the other computers IP address and share directory (if needed). Click okay, if you need authentication, the auth box will appear, add your username & password, clear the domain box and click save password forever (only do this in private use, otherwise anyone can dive into the other computer through the share).

---

