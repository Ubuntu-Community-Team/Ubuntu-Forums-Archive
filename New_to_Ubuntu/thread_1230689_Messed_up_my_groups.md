---
title: "Messed up my groups"
date: 2009-08-03
forum: New to Ubuntu
---

### Post by I[AM]SMRT on 2009-08-03
So I was trying to add myself to a group with "usermod -a -G <group> <user>" and I accidentally removed myself from all of the secondary groups I was a part of. Now when I try a sudo command, it tells me that I'm "not in the sudoers file" what can I do?

-SMRT

---

### Post by oldos2er on 2009-08-03
[http://psychocats.net/ubuntu/fixsudo](http://psychocats.net/ubuntu/fixsudo)

---

### Post by I[AM]SMRT on 2009-08-03
I figured it out, had to boot in recovery mode and did:

```
sudo visudo
```

and added my user to the file as in:

```
brian  ALL=(ALL) ALL
```

but then removed it once I changed my groups back (luckily I had backed up earlier today so that I have all my groups back now).

---

