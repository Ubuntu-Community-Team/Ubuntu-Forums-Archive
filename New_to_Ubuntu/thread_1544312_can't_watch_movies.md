---
title: "can't watch movies"
date: 2010-08-02
forum: New to Ubuntu
---

### Post by geekette2010 on 2010-08-02
I can't watch movies in ubuntu. I tried to put in VLC and it said I need plugins.  Can someone help? thanx in advance  geekette

---

### Post by eddietours on 2010-08-02
you may need the ubuntu-restricted-extras

---

### Post by LowSky on 2010-08-02
install the medibuntu repo
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update && sudo apt-get --yes install app-install-data-medibuntu apport-hooks-medibuntu
```


then install libdvdcss2
```
sudo apt-get install libdvdcss2
```

---

### Post by geekette2010 on 2010-08-02
checking it out 

Thanx,
geekette

---

### Post by geekette2010 on 2010-08-02
> **LowSky said:**
> install the medibuntu repo
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update && sudo apt-get --yes install app-install-data-medibuntu apport-hooks-medibuntu
```then install libdvdcss2
```
sudo apt-get install libdvdcss2
```
this one worked  

sudo apt-get install w32codecs 
for movie player in th software center.

---

### Post by samchn07 on 2011-11-13
You can easily   install VLC in ubuntu, just google around.

---

