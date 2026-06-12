---
title: "where to save ssh keys?"
date: 2010-12-24
forum: New to Ubuntu
---

### Post by philipballew on 2010-12-24
i have made a pair of ssh keys to connect from my laptop to my server. i am living th the residence of the server and figure putting the key onto a flash drive then copying it over would be good, however how can i copy paste on terminal and where would i save the .pub key in my Ubuntu server edition?

---

### Post by CharlesA on 2010-12-24
You can use [ssh-id-copy]("http://linux.die.net/man/1/ssh-copy-id") to add the keys to a remote machine.

Public keys are stored in ~/.ssh/authorized_keys

---

### Post by philipballew on 2010-12-24
is it bast to enable paswords just for logging in to save the key or put the key on a flash drive and copy paste it in

---

### Post by CharlesA on 2010-12-24
If you can connect to the box, you can copy/paste it into ~/.ssh/authorized_keys.

Either that or just cat the public key into the authorized_keys file:

```
cat id_rsa.pub >> ~/.ssh/authorized_keys
```

---

### Post by philipballew on 2010-12-24
does the cat command know where the pub file is(it will be on my flash drive)?

---

### Post by CharlesA on 2010-12-24
No. You'd have to run cat from the directory the public key is in, or tell cat where to find it:

```
cat /path/to/public/key >> ~/.ssh/authorized_keys
```

---

