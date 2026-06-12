---
title: "Add user to server doesn't add user to NIS"
date: 2008-11-24
forum: Networking &amp; Wireless
---

### Post by minime283 on 2008-11-24
Hey guys,
So I setup NIS and started adding users, but all users I've added since I've installed it aren't reflected in NIS. I'm not sure if this is the way it's supposed to be? Am I missing a step? Should I be calling some refresh function? Or should I be adding users directly to NIS?

Extra info. Server: 8.04 Client: Xubuntu 8.04. I can log in with at least one username and password using NIS.

---

### Post by ikarpov on 2009-09-05
There are two things you may be missing:

Thing one: update the server's NIS information:

```

sudo make -C /var/yp

```

Thing two: restart nis and portmap services on the server (and possibly also client). You can do this either by restarting the systems or by calling:

```

sudo /etc/init.d/portmap restart
sudo /etc/init.d/nis restart

```

HTH

---

