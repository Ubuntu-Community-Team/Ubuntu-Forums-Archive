---
title: "k3b and k9copy installation problem"
date: 2010-06-09
forum: New to Ubuntu
---

### Post by chuckycheese on 2010-06-09
here's dummy again,  installed 10.4, clean install,  k3b and k9 copy are not in the repo, so I downloaded them, now I have a tar.bz2 and tar.gz files,  the readme files make not sense, In Ubuntu 9 I thought I found them in the repo, IDK

---

### Post by mbzn on 2010-06-09
Try downloading the .deb files for x64 here [http://packages.ubuntu.com/lucid/amd64/k3b-dbg/download](http://packages.ubuntu.com/lucid/amd64/k3b-dbg/download)

When looking for packages in google enter .deb at the end, it just much easier

---

### Post by TeoBigusGeekus on 2010-06-09
Have you tried 
```
sudo apt-get install k3b
```

---

### Post by oldos2er on 2010-06-09
Check System, Administration, Software Sources to make sure you have all repositories enabled, then run ```
sudo apt-get update && sudo apt-get install k3b k9copy
```

---

### Post by Tholley on 2010-06-09
Here is a great link for setting everything up. It will guide you thru enabling all the right repositories along alot of other useful info! :p
 
[http://sites.google.com/site/easylinuxtipsproject/Home](http://sites.google.com/site/easylinuxtipsproject/Home)

---

### Post by chuckycheese on 2010-06-10
Thanks all, ann' worked, I couldn't use the x64. I am running 32-bit

---

