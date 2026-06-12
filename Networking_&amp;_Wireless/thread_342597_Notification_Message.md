---
title: "Notification Message"
date: 2007-01-20
forum: Networking &amp; Wireless
---

### Post by ksamvel on 2007-01-20
Suppose I have several computers in my home network. Each of them is running Linux (Kubuntu 6.10) with ssh server enabled. Say, some user is logged in to Desktop machine. I am working with my laptop and was requested by mentioned above user to install some program on Desktop. So, I log into Desktop via ssh and do my job. The point is that I would like to be able to notify user once installation process is done. I know it is possible in Windows to send a message to a particular machine in network. How to do that in Linux?

Thanks.

---

### Post by kasper22 on 2007-01-28
I'm looking for the same thing.  There has to be a way to do this.  I hope someone with the know how sees this an pipes in.

---

### Post by ksamvel on 2007-02-02
Use next with ssh:

```
DISPLAY=:0.0 xmessage -buttons "Thanks" -default "Thanks" -center "Maintenance completed"
```

---

### Post by kasper22 on 2007-02-03
ksamvel very cool, thanks for letting me know why you found.

---

