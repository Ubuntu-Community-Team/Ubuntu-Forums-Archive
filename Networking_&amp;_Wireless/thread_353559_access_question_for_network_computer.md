---
title: "access question for network computer"
date: 2007-02-04
forum: Networking &amp; Wireless
---

### Post by rabid9797 on 2007-02-04
so from my windows computer, under the microsoft windows netowork, i can see my ubuntu computer, but when i try to access it, im asked for a username and password. problem is, i never setup a username or password on my ubuntu comp for accessing it. 

so how would i find the username and pw to let my windows computer access ubuntu comp?

[img]http://xs412.xs.to/xs412/07061/problem.JPG[/img]

---

### Post by rabid9797 on 2007-02-04
halp!

---

### Post by PilotJLR on 2007-02-04
you need to setup a user in samba. do this:
```

sudo smbpasswd (username)

```

Of course, replace (username) with your username  :-)

Keep in mind, you will then have to provide your password for root (sudo) access... then you enter a new password (can be the same, if you want) to create the samba password.

---

### Post by rabid9797 on 2007-02-04
thanks! that got it working!

---

