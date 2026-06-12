---
title: "ssh server?"
date: 2008-01-21
forum: Networking &amp; Wireless
---

### Post by Geran on 2008-01-21
Just wondering how to get my ssh server started on my computer. I've tried to ssh into it from inside my private network, but it gives the "port 22: connection refused" error. Someone else had this problem and fixed it by starting their ssh server somewhere. where is that?

---

### Post by benanzo on 2008-01-21
If you're getting "Connection Refused" instead of "Permission Denied" then you've likely got a firewall configuration issue.  You need to forward port 22 from your router to the machine that you want to connect to.

You can start, stop or restart the ssh service by doing:
```
sudo /etc/init.d/ssh restart # or stop/start
```

---

### Post by Geran on 2008-01-21
Nah, I found it, it was the funny fact that I didn't have ssh installed.

Solution was sudo apt-get install openssh-server

Problem solved.

---

