---
title: "How do I get permission to use my evolution files?"
date: 2009-09-17
forum: New to Ubuntu
---

### Post by bwallum on 2009-09-17
Hi

I have just copied my .evolution folder from one Ubuntu system to another on a separate hard drive.

I can see contacts and emails ok. When I try to access an email folder I'm told> Cannot create folder lock on /home/bobusb/.evolution/mail/local/Inbox: Permission denied

Looks like it's a quick fix, can you tell me how please?

---

### Post by sisco311 on 2009-09-17
You have to change the owner of the directory.

Open a terminal (Applications -> Accessories -> Terminal)
and type (or even better copy/paste ;) ):
```
sudo chown -R bobusb\: /home/bobusb/.evolution/
```

---

### Post by bwallum on 2009-09-17
Hole in one! Thanks sisco311!

---

