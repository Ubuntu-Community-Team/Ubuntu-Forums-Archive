---
title: "Update ubuntu in command line"
date: 2009-04-28
forum: New to Ubuntu
---

### Post by Drenriza on 2009-04-28
How do you update ubuntu to 9.04 by only using the command line interface?
i've tryed sudo apt-get dist-upgrade but that dosen't work. Then how do u do it?

Regards Dren

---

### Post by oOarthurOo on 2009-04-28
Try this:
```
sudo apt-get install update-manager-core
sudo do-release-upgrade
```

---

### Post by mcduck on 2009-04-28
```
sudo do-release-upgrade
```

"apt-get dist-upgrade" doesn't mean upgrading to next distribution release. it means upgrading your *current* distribution.

Simple "upgrade" allows upgrading packages, and if necessary, installing additional packages. "dist-upgrade" works like "upgrade", but in addition allows removing packages when needed.

In GUI, the Update manager works like "apt-get upgrade", while upgrading in Synapticworks like "dist-upgrade".

---

### Post by Drenriza on 2009-04-28
Thanks :) now it's working, but.
What does (do) mean? what does it do?.

I can see it's working but im couries why it's working.

---

### Post by mcduck on 2009-04-28
> **Drenriza said:**
> Thanks :) now it's working, but.
What does (do) mean? what does it do?.

I can see it's working but im couries why it's working.

"do-release-upgrade" is just the name the developers gave to the program that does release upgrades from command line.

---

### Post by gatoguts on 2010-02-13
I tried sudo do-release-upgrade but am getting "No new release found" How can this be if I only have 8.04?  Could it be a hardware issue? (I have a Dell mini-laptop that came pre-equipped with 8.04)

---

### Post by Elfy on 2010-02-13
No - you have an LTS the new LTS is not released as yet.

Thread closed - if you need to ask more please start a new thread.

---

