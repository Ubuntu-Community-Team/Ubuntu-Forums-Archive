---
title: "upgrade to PHP 5.3 problems. (php5-dev)"
date: 2010-03-01
forum: New to Ubuntu
---

### Post by InfernalAngel on 2010-03-01
I had tried to upgrade from PHP 5.2 to PHP 5.3 using dotdeb repository. Things seem working fine so far but now I want to install the php5-dev then it said sth about conflict with libtool (sth like conflict/or required don't remember with libtool >=2.2.2 ... i don't remember correctly), anyone plz help me out with this issue please

---

### Post by allenru on 2010-03-29
Try to manually downgrade libtool
```

cd /tmp
wget http://cz.archive.ubuntu.com/ubuntu/pool/main/libt/libtool/libtool_1.5.26-1ubuntu1_i386.deb
sudo apt-get remove libtool
sudo dpkg -i libtool_1.5.26-1ubuntu1_i386.deb

sudo apt-get install php5-dev
```It worked for me just fine

---

### Post by elion on 2010-10-16
thx, works for me on kubuntu karmic

---

