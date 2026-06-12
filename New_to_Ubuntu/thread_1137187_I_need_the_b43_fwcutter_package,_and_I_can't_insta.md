---
title: "I need the b43 fwcutter package, and I can't install it"
date: 2009-04-25
forum: New to Ubuntu
---

### Post by Asterio on 2009-04-25
I need the b43 fwcutter package for my wireless card to work. Normally, I could just install it from the Hardware Driver window, but a search for drivers through that window turns up nothing. 

I've googled it, and found it, but I don't know what to do with a tar.gz file. 

I need some help.

I'm running Jaunty, if that means anything at all.

---

### Post by zvacet on 2009-04-25
Untar package with right click on it or in terminal with 

```
tar zxvf package.tar.gz
```

You will see folder and inside probably **install fil**e or **read me file.**

---

### Post by tommynz1975 on 2009-04-25
failing that try

in terminal
```
sudo apt-get install b43-fwcutter
```

---

