---
title: "Windows Sharing and Firewalls"
date: 2011-06-10
forum: New to Ubuntu
---

### Post by John Peschken on 2011-06-10
I would like to run a firewall on my Ubuntu computer, but every time I start up a firewall I lose contact with my wife's Windows box.  I suspect there are ports or protocols I need to allow, but apparently I am not picking the correct ones.  Go easy on me, I'm new at this manually configuring firewalls stuff.

---

### Post by collisionystm on 2011-06-10
> **John Peschken said:**
> I would like to run a firewall on my Ubuntu computer, but every time I start up a firewall I lose contact with my wife's Windows box.  I suspect there are ports or protocols I need to allow, but apparently I am not picking the correct ones.  Go easy on me, I'm new at this manually configuring firewalls stuff.


Open TCP/UDP ports 138 and 139

---

### Post by HermanAB on 2011-06-10
...or just open port 445.

Old versions of Windows used 138 and 139.  Later versions added 445.

---

### Post by John Peschken on 2011-06-11
> **HermanAB said:**
> ...or just open port 445.

Old versions of Windows used 138 and 139.  Later versions added 445.

Thanks!  445 was the magic number.

---

