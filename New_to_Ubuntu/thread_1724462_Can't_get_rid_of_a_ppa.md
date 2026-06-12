---
title: "Can't get rid of a ppa"
date: 2011-04-08
forum: New to Ubuntu
---

### Post by maembe on 2011-04-08
I have this stupid repository that won't go away and whenever I try apt-get update it returns with:  
W: failed to fetch [http://ppa.launchpad.net/aheck/ppa/ubuntu/dists/maverick/main/source/Sourcez.gz](http://ppa.launchpad.net/aheck/ppa/ubuntu/dists/maverick/main/source/Sourcez.gz) 404 Not Found
E: Some Index files failed to download, they have been ignored or older ones used instead

I was able to get rid of other ppas I didn't need with the kpackage kit but I can't seem to find this one.   Is there a command I can use for this?

---

### Post by Frogs Hair on 2011-04-08
You should be able to delete the source from your software sources list . [https://help.ubuntu.com/community/Repositories/Kubuntu](https://help.ubuntu.com/community/Repositories/Kubuntu)

---

### Post by maembe on 2011-04-08
Jeez, that was easy.
Thanks

---

### Post by Frogs Hair on 2011-04-08
You're welcome !

---

