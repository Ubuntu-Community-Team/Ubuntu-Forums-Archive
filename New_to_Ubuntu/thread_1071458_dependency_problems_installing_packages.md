---
title: "dependency problems installing packages"
date: 2009-02-16
forum: New to Ubuntu
---

### Post by cosmicappuccino on 2009-02-16
I am trying to install g++ (g++_4.2_4.2.4-1ubuntu3), and I am getting a message saying:

> Error: Dependency is not satisfiable: libstdc++6-4.2-dev

So, I downloaded libstdc++6-4.2-dev_4.2.4-1ubuntu3, but when I try to install that, I get a message saying:

> Error: Dependency is not satisfiable: g++-4.2

How am I meant to install either of them?! :confused: Am I doing something wrong?

Any thoughts, please?

---

### Post by stumbleUpon on 2009-02-16
> **cosmicappuccino said:**
> I am trying to install g++ (g++_4.2_4.2.4-1ubuntu3), and I am getting a message saying:



So, I downloaded libstdc++6-4.2-dev_4.2.4-1ubuntu3, but when I try to install that, I get a message saying:



How am I meant to install either of them?! :confused: Am I doing something wrong?

Any thoughts, please?

How are you installing them...? Manually...?

Install via synaptic or aptitude. This takes care of all the dependencies. 

See here for how to do this.

[https://help.ubuntu.com/8.10/add-applications/C/index.html](https://help.ubuntu.com/8.10/add-applications/C/index.html)

---

### Post by cosmicappuccino on 2009-02-16
Thanks, it worked :)

---

