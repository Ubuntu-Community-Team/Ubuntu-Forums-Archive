---
title: "Problems upgrading to 10.10"
date: 2011-02-20
forum: New to Ubuntu
---

### Post by TriBlox6432 on 2011-02-20
All I had on hand was a 10.04 CD and now I'm trying to upgrade.  I already installed all the updates.

---

### Post by J697 on 2011-02-20
So your on 10.04 LTS then? Well at what point of the install does this pop up? What happens before/after it does pop up? The more info you provide, the more everybody can see whats wrong. ;)

---

### Post by deconstrained on 2011-02-20
Maybe "dpkg --yet-to-unpack" would show you where the problem is - and that's a maybe. Since it's a release upgrade you're running instead of an ordinary update, it's not just dpkg that could be messing up, but something in Ubuntu's special release upgrade system.

---

### Post by TriBlox6432 on 2011-02-21
The problem happened on the second stage of the upgrade.  I don't remember what it's called exactly.  But it failed thrice so far . . .

---

### Post by TriBlox6432 on 2011-03-04
Bump.

---

### Post by TriBlox6432 on 2011-03-06
Bump.

---

### Post by TriBlox6432 on 2011-03-10
Bump.

---

### Post by Nickjpost on 2011-03-10
Check your update manager, make sure that all of your software sources are checked in the radio box, including independent sources, then try again

---

### Post by akand074 on 2011-03-10
Then perhaps you can try to run an update from the Terminal, I believe the command is:

```
sudo apt-get upgrade -d
```

It might show additional errors if it doesn't work that might be helpful.

---

