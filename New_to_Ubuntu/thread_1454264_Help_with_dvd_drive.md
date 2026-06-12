---
title: "Help with dvd drive?"
date: 2010-04-14
forum: New to Ubuntu
---

### Post by tsp_2177 on 2010-04-14
Hi, i recently loaded ubuntu on my parents desktop after tinkering with it for a good while in my two laptops i decided that they should be able to handle it no problem. Well i'm having a problem with it besides them now lol. Ok when i inserted a dvd in my laptop it told me that i needed to install dvdlib i think? well my ubuntu expert told me about all that and i understand why i need to have that on there because it doesn't come with ubuntu. So that all worked fine, and i was able to wathc dvds no problem on my laptop. Well now my problem is when i inserted it in the newly installed desktop, i could hear the disk spin, but nothing every popped up about installing the dvdlib or anything it just sat there and spun for like an hour. Well i went to synaptic package manager and installed what i thought was right but it still does nothing when i insert a DVD, can anyone help me figure out whats wrong? i look under places and it doesn't show anything, i look under computer and click on dvd drive and it does nothing, just wondering if anyone is experiencing the same problems as me. 
thanks in advanced.

---

### Post by Sef on 2010-04-14
Go to the [medibuntu repositories]("http://www.medibuntu.org/") to get the drivers for playing dvds.

---

### Post by Garudi on 2010-04-14
Problem is, that repository howto link doesn't work at the moment.

---

### Post by Fuith on 2010-04-14
Go to System->Administration->Software Sources and check the multiverse box. Next open a terminal and type the following:

```
sudo apt-get update

sudo apt-get install ubuntu-restricted-extras
```

---

### Post by tsp_2177 on 2010-04-14
> **Fuith said:**
> Go to System->Administration->Software Sources and check the multiverse box. Next open a terminal and type the following:

```
sudo apt-get update

sudo apt-get install ubuntu-restricted-extras
```
 
ok thank you i will try that when i get home

---

### Post by tsp_2177 on 2010-04-14
still a no go guys any other thoughts?

---

