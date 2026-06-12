---
title: "Need help using Alien to convert rpm to deb"
date: 2009-12-04
forum: New to Ubuntu
---

### Post by username22 on 2009-12-04
I'm trying to convert the followin on ubuntu 9.10 to a deb file:
 pidgin-gfire-0.8.3-1.fc12.i686.rpm
So i installed Alien to convert it to a .deb file. I tried
sudo alien
sudo alien -d
sudo alien -i
sudo alien -k

I used each command then "pidgin-gfire-0.8.3-1.fc12.i686.rpm" but when i do that, all of them give the same result: 
File pidgin-gfire-0.8.3-1.fc12.i686.rpm not found.

Any ideas on what i'm doin wrong?

---

### Post by bodhi.zazen on 2009-12-04
"what i'm doin wrong?" is a broad question, and I can not resist :

First, you should install that from the Ubuntu repositories :

```
sudo apt-get install gfire
```[http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=gfire](http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=gfire)

[InstallingSoftware - Community Ubuntu Documentation]("https://help.ubuntu.com/community/InstallingSoftware") 

Second, alien is not such a great idea, it can cause problems, and IMO used only as a last resort. I would compile from source b4 using alien.

Last, you need to put the full path for your RPM. Is it on Desktop ?

alien -d ~/Desktop/pidgin-gfire-0.8.3-1.fc12.i686.rpm

---

