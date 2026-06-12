---
title: "How to install ...."
date: 2010-05-31
forum: New to Ubuntu
---

### Post by saakeman on 2010-05-31
How to install the mxit pidgin plug-in

there is a plug-in on the pidgin site for mxit but are unable to install it 

how to do this 
will really like to talk to my mxit buddy's

---

### Post by cariboo on 2010-05-31
I don't use pidgin, but [these]("http://ubuntica.com/use-mxit-on-ubuntu.html") instructions may help.

---

### Post by marshmallow1304 on 2010-05-31
According to [this page]("http://devzone.mxit.com/libPurple/downloads/"), the latest version of Pidgin has built in support for mxit.  [This page]("http://pidgin.im/download/ubuntu/") will help you install the latest version of Pidgin.

---

### Post by saakeman on 2010-06-01
> **marshmallow1304 said:**
> According to [this page]("http://devzone.mxit.com/libPurple/downloads/"), the latest version of Pidgin has built in support for mxit.  [This page]("http://pidgin.im/download/ubuntu/") will help you install the latest version of Pidgin.

I have the newest version and it does not have it there on the list

---

### Post by saakeman on 2010-06-01
> **cariboo907 said:**
> I don't use pidgin, but [these]("http://ubuntica.com/use-mxit-on-ubuntu.html") instructions may help.


may I ask , what do you use ?

---

### Post by marshmallow1304 on 2010-06-01
> **saakeman said:**
> I have the newest version and it does not have it there on the list

Are you sure?  The version in the Ubuntu repositories is not the newest version.
```
pidgin --version
```
The version in the Ubuntu repositories is 2.6.6.  The newest is 2.7.0.

To install the newest version:
```
sudo add-apt-repository ppa:pidgin-developers/ppa
sudo apt-get update
sudo apt-get upgrade
```

---

