---
title: "installing prey anti theft client on natty"
date: 2011-06-05
forum: New to Ubuntu
---

### Post by skyzthelimit230 on 2011-06-05
Hello,
so through Synaptic Package Manager, I installed prey 4.4.1. Problem is, I can't configure the client on my Ubuntu 11.04 machine. I already have a Prey account (I have been using prey on my windows comps for some time now). But I can't seem to open prey on my linux comp to configure; in fact, searching for prey dosent even yield prey.

Where did I go wrong?

---

### Post by jtarin on 2011-06-05
In terminal update your database to locate new files. ```
sudo updatedb
``` then use the command ```
locate <nameoffile> 
```

---

### Post by jtarin on 2011-06-05
If you have it installed enter this command```
/usr/lib/prey/prey.sh  /usr/lib/prey/prey.sh --check mode enabled
```

---

