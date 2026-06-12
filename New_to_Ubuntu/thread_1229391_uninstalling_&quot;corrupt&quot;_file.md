---
title: "uninstalling &quot;corrupt&quot; file"
date: 2009-08-02
forum: New to Ubuntu
---

### Post by alpha78 on 2009-08-02
(Jaunty)

I tried to install 'bandwidthd 2.01' and got a return message that the package was in bad condition and did not install.

Now it is stuck in the queue as I am unable to remove it nor install it as I get the same message about the package in bad condition. You cannot uncheck the box either.

So every time I update anything this is run through the ringer again and I'm sick of it.

48 hours into ubuntu and having great fun, but stuck on this one and need help plz.

tnx

ubunewb

---

### Post by Malta paul on 2009-08-02
You can try going to System>Administration>Synaptic package manager, search for your file. then click remove.& apply.
That should work :D

---

### Post by alpha78 on 2009-08-02
That does not work. 

I mark for removal or complete removal and it comes back "package is in a bad inconsistent state" and fails to remove.

---

### Post by MelDJ on 2009-08-02
try sudo apt-get remove* filename* in terminal

---

### Post by alpha78 on 2009-08-02
same story in terminal:
"package in a bad inconsistent state, you should install it before trying to remove it."

---

### Post by Dark Aspect on 2009-08-02
Maybe

```
sudo apt-get --fix-broken
or 
sudo apt-get --fix-missing
```

---

