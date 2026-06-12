---
title: "The Opera (File Edit View ect.,) bar is driving me NUTS!"
date: 2009-10-07
forum: New to Ubuntu
---

### Post by R3fr4cti0n on 2009-10-07
i have changed the theme a dosen times and tried everything els but it wont change from that old windows basic gray look i just want ti to match my theme weather it be my Ubuntu theme or the theme of Opera. i read some where that i can have the drop down menus even be transparent and such so any one know how to do this?

btw it oper 10 and i am running 9.04
thanks!

---

### Post by R3fr4cti0n on 2009-10-07
anyone even use opera anymore?

---

### Post by R3fr4cti0n on 2009-10-08
bump for the Euro shift

---

### Post by Arup on 2009-10-08
Plenty of Opera users, Opera is an excellent browser once setup right. Can you tell me what version you are using for Opera? Have you tried qt4 version by any chance?

---

### Post by R3fr4cti0n on 2009-10-08
i dont know what qt4 is but i am using opera 10 if it matters any i am using 64bit 9.04 ubuntu

---

### Post by Arup on 2009-10-08
> **R3fr4cti0n said:**
> i dont know what qt4 is but i am using opera 10 if it matters any i am using 64bit 9.04 ubuntu

Do a sudo apt-get --purge remove opera and then download latest opera from [http://snapshot.opera.com/unix/snapshot-4644/x86_64-linux/opera_10.10.4644.gcc4.qt4_amd64.deb](http://snapshot.opera.com/unix/snapshot-4644/x86_64-linux/opera_10.10.4644.gcc4.qt4_amd64.deb)

Install and see if the problem persists or goes away.

---

### Post by R3fr4cti0n on 2009-10-08
yesssss....
thankyou
but what was the problem?

---

### Post by Arup on 2009-10-08
> **R3fr4cti0n said:**
> yesssss....
thankyou
but what was the problem?

Ubuntu uses qt4 and your Opera used qt3 which doesn't blend with your current theme, thankfully they came out with qt4 version which solves the issue.

---

