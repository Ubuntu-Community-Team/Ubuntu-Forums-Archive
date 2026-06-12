---
title: "How to open ports"
date: 2009-02-15
forum: New to Ubuntu
---

### Post by jonw860 on 2009-02-15
I have rtorrent running on a server and I was wondering how do I open up a port for rtorrent to seed with?

---

### Post by BlakeM on 2009-02-15
It depends on your network topology. If your network is behind a router, you'll need to login to your router's interface and open the port. This varies between routers. The best place to find out how to do this is [http://portforward.com/](http://portforward.com/). It has guides for almost every router on how to open ports.

You'll also need to open the port on any software firewall if you have one. Firewall is disabled by default in ubuntu.

---

### Post by Xiong Chiamiov on 2009-02-15
If you would like to use a software firewall in Ubuntu, [ufw](https://wiki.ubuntu.com/UbuntuFirewall) is pretty nice.

---

### Post by Paqman on 2009-02-15
> **Xiong Chiamiov said:**
> If you would like to use a software firewall in Ubuntu, [ufw](https://wiki.ubuntu.com/UbuntuFirewall) is pretty nice.

And it even has a nice GUI version called Gufw.

---

### Post by BlakeM on 2009-02-15
+1 for ufw and gufw. Both easily configured for noobs like me.

---

