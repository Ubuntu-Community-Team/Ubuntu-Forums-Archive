---
title: "Warzone 2100"
date: 2009-12-01
forum: New to Ubuntu
---

### Post by OwNeD on 2009-12-01
how can i install Warzone 2100  the latest version on ubuntu 9.10 ?

 and what file should i download?

---

### Post by nothingspecial on 2009-12-01
```
sudo apt-get install warzone2100
```

---

### Post by marshmallow1304 on 2009-12-01
You can add the [PlayDeb]("http://www.playdeb.net") repository, as they have the latest version (2.2.4).

> 
Go to System-Administration-Software Sources, Third-Party Software tab, Add:
```
deb http://archive.getdeb.net/ubuntu karmic-getdeb games
```

Add the repository GPG key, open a terminal window and type:
```
wget -q -O- http://archive.getdeb.net/getdeb-archive.key | sudo apt-key add -
```


Then, if you've already installed it,
```
sudo apt-get update
sudo apt-get upgrade
```

If you haven't,
```
sudo apt-get update
sudo apt-get install warzone2100
```

---

### Post by OwNeD on 2009-12-02
Thanks!

---

### Post by aharown07 on 2009-12-09
I installed wz2100 via playdeb.net using apturl... so didn't add the repository (not manually anyway).
But synaptic says the ver of the game I have now is 2.2.2

(Also... anybody know how to reach the playdeb folks? Their contact page just results in 500 server error.)

---

### Post by BLXX on 2009-12-09
Oh wow, I'd forgotten about WarZone 2100.  Great thread!

---

