---
title: "Icons Changed"
date: 2009-01-20
forum: New to Ubuntu
---

### Post by chethankrish on 2009-01-20
hi..  what does the option suspend do?????

and whats the difference between suspend and hibernate???

---

### Post by jimmy the saint on 2009-01-20
What does the title of your thread have to do with your question?  Please use descriptive post titles that are relevant to your questions.

Hibernate copies your current session (the contents of your RAM) to the harddrive and powers down the machine completely.  Upon resuming, the RAM is restored to its previous state so that you can pick up where you left off.  In order to perfrom this, you need to have a swap partition with more space than you have RAM.

Suspend mostly powers down the machine, but continues to draw enough power to keep the RAM active so that you don't lose your current state.  It draws far less power in this state because ONLY they RAM is powered, not the HD, not the processor, GPU, fans etc.

They are alternatvives to shutting down your computer completely and having to boot it up when you want to start working again.

---

