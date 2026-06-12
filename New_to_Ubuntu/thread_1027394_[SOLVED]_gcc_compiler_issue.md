---
title: "[SOLVED] gcc compiler issue"
date: 2009-01-01
forum: New to Ubuntu
---

### Post by sanubie on 2009-01-01
For some reason, gcc won't compile on my Dell Mini 9. gcc appears to be installed, because it reacts, but it keeps giving me errors. It even says stdio.h doesn't exist. So I'm thinking I'm missing something. Any ideas?

---

### Post by gila_monster on 2009-01-01
Have you installed build_essentials?

---

### Post by sanubie on 2009-01-01
> **gila_monster said:**
> Have you installed build_essentials?

I'm not entirely sure. I assumed it would be there by default. But it's a mini, so maybe not. Come to think of it, I'm not sure if I had to install it on my desktop or not. I think it was on my main computer by default. 

How do I install the build essentials? Is it isn the repositories? Can I install from terminal?

---

### Post by Joeb454 on 2009-01-01
run ```
sudo apt-get install build-essential
``` if you want to install it from a terminal :)

---

