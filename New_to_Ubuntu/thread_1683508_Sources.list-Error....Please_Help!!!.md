---
title: "Sources.list-Error....Please Help!!!"
date: 2011-02-07
forum: New to Ubuntu
---

### Post by jimmyBoy18 on 2011-02-07
When I tried to run the Updater I got a big, ugly red circle with a white dash in it and the following message...

E: Malformed line 59 in source list /etc/apt/sources.list (dist parse)
E: Unable to lock the list directory

I ran this command...gksudo gedit /etc/apt/sources.list...and got this output @ line 59:

deb [http://archive.canonical/lucid](http://archive.canonical/lucid) partner
deb-src [http://archive.canonical/lucid](http://archive.canonical/lucid) partner

Can anyone help me? Thanks.

---

### Post by jimmyBoy18 on 2011-02-07
OK...Nevermind. I fixed it by editing the file in gedit. Thanks...

---

### Post by ajgreeny on 2011-02-07
Did you just delete it or correct it to what it should be?
```
deb http://archive.canonical.com/ubuntu lucid partner
deb-src http://archive.canonical.com/ubuntu lucid partner
```

---

