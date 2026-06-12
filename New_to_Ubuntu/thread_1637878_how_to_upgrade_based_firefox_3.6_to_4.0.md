---
title: "how to upgrade based firefox 3.6 to 4.0"
date: 2010-12-05
forum: New to Ubuntu
---

### Post by Unix3r on 2010-12-05
Hello
how to upgrade the firefox in ubuntu to 4.0
thanks

---

### Post by waynefoutz on 2010-12-05
```
sudo add-apt-repository ppa:ubuntu-mozilla-daily/ppa 

sudo apt-get update

sudo apt-get install firefox-4.0
```




If you get an error:

```
sudo ln -s /usr/lib/firefox-4.0b2pre/firefox-4.0 /usr/bin/firefox-4.0

sudo apt-get -f install
```

---

