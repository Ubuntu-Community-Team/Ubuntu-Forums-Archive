---
title: "samba shares an ufw"
date: 2009-09-13
forum: New to Ubuntu
---

### Post by shanep-server on 2009-09-13
I am having a problem sharing between 2 ubuntu machines an a windows xp machine. If i have ufw disabled on both ubuntu machines I can see all computers an transfer between all of them. The second I turn on ufw nothing works xp can't get into ubuntu shares and ubuntu shares can't see anything.

I tried to open up the ports for udp an tcp for samba but that still won't work. Only way I can share is with ufw completely turned off. 

What do I need to do ? If u need too see how my config files look I would be more then happy to show if needed.

Thank u for your time.

---

### Post by pedja_portugalac on 2009-09-13
Take a look: [http://ubuntuforums.org/showthread.php?t=806000](http://ubuntuforums.org/showthread.php?t=806000)

---

### Post by shanep-server on 2009-09-13
ty i used that before but I forgot to configure /etc/default/ufw now everything seems to be working fine.

---

