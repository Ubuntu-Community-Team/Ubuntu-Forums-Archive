---
title: "Apache stops responding"
date: 2007-06-25
forum: Networking &amp; Wireless
---

### Post by jokkum1991 on 2007-06-25
Ok, i've got this strange problem...
After a few minutes, Apache stops responding! Though, if i log on the server (via VNC or just opening a SSH session) it works like a charm for a few minutes, but if there's no activity it stops responding again...
The server is running Ubuntu 6.06 LTS (desktop).
Anybody knows what's wrong? I heard about another guy having about exactly the same problem on a almost identical system...

---

### Post by rklauco on 2007-06-25
Well, check the server log in /var/log/apache.
Else, try googling for any error message found.
And, the best place for you will probably bee the apache mailing list...

---

### Post by jokkum1991 on 2007-06-27
Ok, i hasn't checked the log yet, but i simply opened a screen session on the server (which i keep attached in Putty on my windows box), and now it's working fine! So the problem is, at least temporarily, solved..

---

