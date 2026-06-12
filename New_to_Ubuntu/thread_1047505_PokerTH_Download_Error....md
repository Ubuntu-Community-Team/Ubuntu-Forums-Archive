---
title: "PokerTH Download Error..."
date: 2009-01-22
forum: New to Ubuntu
---

### Post by Leo Dragonheart on 2009-01-22
I tried downloading PokerTH and I get this error. also when I went to take the screen shot it opened screen shot 20 times and I only hit the key once. Can any one help me with this please?

---

### Post by bwang on 2009-01-22
Seems like you also need the pokerth-data package on [this site]("http://ppa.launchpad.net/sargentd/ubuntu/pool/main/p/pokerth/")

---

### Post by Technoviking on 2009-01-22
Add the following ppa to your software sources
```
deb http://ppa.launchpad.net/sargentd/ubuntu intrepid main
```

Update repo list, then install
```
sudo apt-get update
sudo apt-get install pokerth
```

---

### Post by Leo Dragonheart on 2009-01-23
I have tried the above and still can't seem to get it. I am sure I am doing something wrong, could I please have some detailed step by step instructions please... Thank you....

---

