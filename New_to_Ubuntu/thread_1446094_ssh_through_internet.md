---
title: "ssh through internet"
date: 2010-04-03
forum: New to Ubuntu
---

### Post by werecatomega on 2010-04-03
hey guys

i want to connect to my mac box via ssh through the internet (aka [ubuntu box] {router a} internet {router b} [mac box]) but i'm not sure what i should do

please help

---

### Post by NCLI on 2010-04-03
You'll need to configure your home router to do these things:

1) Assign a static IP address to the box you want to connect to
2) Forward port 22 to that IP address.

---

