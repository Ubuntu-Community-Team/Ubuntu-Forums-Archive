---
title: "ubuntu software center error message"
date: 2010-11-12
forum: New to Ubuntu
---

### Post by rburkartjo on 2010-11-12
i am getting the following error message when i try to install anything from the software center "requires installation of untrusted packages= the action would require the installation of packages from not authenticated sources." note i can still install from spm.
any ideas how to fix, weird

---

### Post by patC42 on 2010-11-12
Try system >Administration>Software sources  ubuntu sources 

Uncheck Proprietry drivers and software restricted. click close and you will be prompted to reload. 

Do this and try to download the software you want.

---

### Post by rburkartjo on 2010-11-12
pat tks fixed problem.

---

### Post by sikander3786 on 2010-11-12
But that way you might not be able to install any proprietary software like some codecs, flash, java, some hardware drivers etc.

You will need to enable them when you need some software like that.

---

### Post by rburkartjo on 2010-11-12
sik how would you have fixed

---

### Post by sikander3786 on 2010-11-12
> **rburkartjo said:**
> sik how would you have fixed
Enable the deselected repositories and again open Software Center. Does it open? If yes, you'r good to go.

It might be fixed by changing the update server from Software Sources, or importing the missing keys or whatever. We need to see the output of this to sort that out.

```
sudo apt-get update
```

Sometimes it is just warning you that the software you are trying to install is not open source or not Canonical developed and maintain. In that case, you can just ignore the warning.

---

### Post by rburkartjo on 2010-11-13
sik that worked like a charm tks

Enable the deselected repositories and again open Software Center. Does it open? If yes, you'r good to go.

---

