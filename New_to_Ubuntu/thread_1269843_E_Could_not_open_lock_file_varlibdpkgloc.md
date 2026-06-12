---
title: "E: Could not open lock file /var/lib/dpkg/loc"
date: 2009-09-18
forum: New to Ubuntu
---

### Post by shadowlands on 2009-09-18
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

Can someone help me with this? I have run sudo getupdate and that worked. bbut the file is still locked.

---

### Post by sandyd on 2009-09-18
to install software, you have to put sudo before the command.

Example:
```

sudo apt-get install avidemux

```
instead of
```

apt-get install avidemux

```

to be honest, ive used sudo apt-get install so much it feels wrong as soon as i type it without the sudo in front:lolflag:

---

### Post by sena_akada on 2009-09-18
if they cannot lock root that wont help. you need to restart the machine.

---

### Post by wojox on 2009-09-18
Try:

```
sudo apt-get update
```

---

### Post by NoaHall on 2009-09-18
Close your update manager, synaptic, and ubuntu-tweak/ultamix and try again.

---

### Post by shadowlands on 2009-09-18
ok trying all suggestions

---

### Post by shadowlands on 2009-09-18
That worked thanks:KS:KS:KS:KS:KS:KS

---

