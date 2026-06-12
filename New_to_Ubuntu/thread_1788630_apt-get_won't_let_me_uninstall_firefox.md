---
title: "apt-get won't let me uninstall firefox"
date: 2011-06-22
forum: New to Ubuntu
---

### Post by Dubslow on 2011-06-22
I'm trying to use apt-get to purge firefox. ('sudo apt-get ourge firefox*') except that it insists on installing chromium, and when I uninstall that it installs firefox again. How do I get it to do what I want it to, without it trying to unnecessarily protect me? I have chrome, so I don't see what its problem is.

---

### Post by jtarin on 2011-06-22
Try to use Synaptic.

---

### Post by Dubslow on 2011-06-22
Workaround. Copy and paste what it tries to install into the same purge command. i.e. sudo apt-get purge A and it tries to install B, so then cancel and do sudo apt-get purge A B and then it installs C, cancel and sudo apt-get purge A B C and on and on until it gave up and removed what I told it to (although it took out icedtea-plugin as well)

---

### Post by Dubslow on 2011-06-22
Synaptic did exactly the same thing apt-get did.

---

### Post by jtarin on 2011-06-22
> **Dubslow said:**
> Workaround. Copy and paste what it tries to install into the same purge command. i.e. sudo apt-get purge A and it tries to install B, so then cancel and do sudo apt-get purge A B and then it installs C, cancel and sudo apt-get purge A B C and on and on until it gave up and removed what I told it to (although it took out icedtea-plugin as well)I recommend Sun Java anyway.....mark this thread as solved it will help someone else.:p

---

### Post by idoitprone on 2011-06-23
i heard it from someone that ubuntu must have a browser of some type. If you uninstall one browser, it will install the other. ubuntu just like adding complexity

---

