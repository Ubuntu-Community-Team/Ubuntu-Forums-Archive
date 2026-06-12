---
title: "cant find liddvdcss2 anywhere in Jaunty Jackalope"
date: 2009-05-07
forum: New to Ubuntu
---

### Post by kapi on 2009-05-07
trying to upgrade a computer and have installed 9.04, All went well but want to install libdvdcss2 in synaptic manager. Medibuntu is installed in software sources, have followed installation guides as mentioned in ubuntu help topics and VLC site. 

Anyone got any ideas please

thanks

---

### Post by riza hylviu on 2009-05-07
type in terminal
sudo apt-get install libdvdcss2

---

### Post by kapi on 2009-05-07
Thanks Riza,

seems to work ok now. It's strange that in synaptic the libdvdcss2 doesn't show up. 

Thanks again - very much appreciated

Kapi

---

### Post by riza hylviu on 2009-05-07
It was not showing in my own too but i found somewhere the command to make them show, i googled around but i just don't remember where i found it:)

---

### Post by LowSky on 2009-05-07
libdvdcss2 isn't in Ubuntu's repos, you need medibuntu
```
sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list --output-document=/etc/apt/sources.list.d/medibuntu.list; sudo apt-get -q update; sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring; sudo apt-get -q update
```


```
sudo apt-get install libdvdcss2
```

---

### Post by doas777 on 2009-05-07
I always install the medibuntu repositories and get my codecs from there, alongside the ubuntu-restricted-extras package.

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

