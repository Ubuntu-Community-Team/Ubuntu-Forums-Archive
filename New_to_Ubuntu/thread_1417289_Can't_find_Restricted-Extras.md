---
title: "Can't find Restricted-Extras"
date: 2010-02-27
forum: New to Ubuntu
---

### Post by virtualsamana on 2010-02-27
I searched for it through Synaptic and the terminal with the command line below. Nothing. Anyone know what happened?

sudo apt-get install ubuntu-restricted-extras

----------------
Karmic
1.3 Ghz Celeron
1 GB RAM

---

### Post by mechro on 2010-02-27
Have you got the "multiverse" repository enabled?

---

### Post by Robster2 on 2010-02-27
Something must have happened when you ran

```
sudo apt-get install ubuntu-restricted-extras
```

What happened?

---

### Post by Soul-Sing on 2010-02-27
> **virtualsamana said:**
> I searched for it through Synaptic and the terminal with the command line below. Nothing. Anyone know what happened?

sudo apt-get install ubuntu-restricted-extras

----------------
Karmic
1.3 Ghz Celeron
1 GB RAM

did you forget to sign licence(s)? as sun java?

---

### Post by Bradtek on 2010-02-27
It's in the Medibuntu Repository isn't it ?

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by alindgr1 on 2010-02-27
That package is in the multiverse repository.  You have to have that enabled for synaptic to find it.  To check this, open Synaptic, click on Settings, and go down to Repositories.  A new window will open.  Ensure the fourth line down that says 

"Software restricted by copyright or legal issues (multiverse)"

is checked.  Click on reload.  Since you already have synaptic open, you can search from there to find it, and install from there.

---

### Post by DeadSuperHero on 2010-02-27
You may need to do "apt-get update" before installing packages sometimes, otherwise it won't find it.

---

