---
title: "Problem with flash player"
date: 2009-08-26
forum: New to Ubuntu
---

### Post by manjotpahwa on 2009-08-26
I went to imeem.com, downloaded flash player 10 for linux (.deb thing), installed it via terminal (sudo apt-get install adobe-flashplugin) then again installed extra plugins but I still can't play music on that site. It says requires flsh player version 9 or more.

---

### Post by jrothwell97 on 2009-08-26
First of all, .deb files are not installed with apt-get. You'd need to run

```
sudo dpkg -i <filename>.deb
```

However, there's a simpler way to install Flash. The package you want is flashplugin-nonfree, so try this:

```
sudo apt-get install flashplugin-nonfree
```

---

### Post by manjotpahwa on 2009-08-26
Hey, thanks a ton! It worked just fine.

---

