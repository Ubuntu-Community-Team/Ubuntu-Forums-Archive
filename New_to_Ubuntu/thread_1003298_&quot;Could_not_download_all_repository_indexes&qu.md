---
title: "&quot;Could not download all repository indexes&quot;"
date: 2008-12-05
forum: New to Ubuntu
---

### Post by Philippe Cambron on 2008-12-05
Hi, I'm new to ubuntu and I get this when I try to update my system.

> Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/universe/binary-lpia/Packages.gz](http://security.ubuntu.com/ubuntu/dists/hardy-security/universe/binary-lpia/Packages.gz)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/main/binary-lpia/Packages.gz](http://security.ubuntu.com/ubuntu/dists/hardy-security/main/binary-lpia/Packages.gz)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/multiverse/binary-lpia/Packages.gz](http://security.ubuntu.com/ubuntu/dists/hardy-security/multiverse/binary-lpia/Packages.gz)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/restricted/binary-lpia/Packages.gz](http://security.ubuntu.com/ubuntu/dists/hardy-security/restricted/binary-lpia/Packages.gz)  404 Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/main/binary-lpia/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hardy/main/binary-lpia/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/universe/binary-lpia/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hardy/universe/binary-lpia/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/multiverse/binary-lpia/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hardy/multiverse/binary-lpia/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/restricted/binary-lpia/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hardy/restricted/binary-lpia/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]
Some index files failed to download, they have been ignored, or old ones used instead.

Can some one help me?

Thanks 
Philippe

---

### Post by collinp on 2008-12-06
Those are probably old/left over mirrors or just ones that are offline atm.. nothing to worry about :).

---

### Post by JC Cheloven on 2008-12-06
> **Philippe Cambron said:**
> Hi, I'm new to ubuntu and I get this when I try to update my system.
Can some one help me?

Thanks 
Philippe

Sometimes some servers are down, incomplete or whatever. I had a similar issue with the spanish server, and solved it choosing another mirror (go to system -> software sources and choose another server to dowload from). After a week, my usual server was ok again.
Hope this helps

---

