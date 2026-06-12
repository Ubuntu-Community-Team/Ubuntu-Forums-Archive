---
title: "how to remove these old back ports"
date: 2009-10-07
forum: New to Ubuntu
---

### Post by DarinB on 2009-10-07
i have an old lap top with hardy running, on updates i get this error how can i remove them
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty-backports/main/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty-backports/main/binary-i386/Packages.gz)  
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty-backports/restricted/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty-backports/restricted/binary-i386/Packages.gz)  
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty-backports/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty-backports/universe/binary-i386/Packages.gz)  
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty-backports/multiverse/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty-backports/multiverse/binary-i386/Packages.gz)  
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty-backports/main/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty-backports/main/source/Sources.gz)  
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty-backports/restricted/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty-backports/restricted/source/Sources.gz)  
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty-backports/universe/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty-backports/universe/source/Sources.gz)  
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty-backports/multiverse/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty-backports/multiverse/source/Sources.gz)  
Some index files failed to download, they have been ignored, or old ones used instead.
it is an old sony with 256mb ram and runs fine for what i need as a back up pc, 
thanks

---

### Post by DarinB on 2009-10-07
on this little lap top it doesn't show but they are all feisty fawn  sources

---

### Post by rbc on 2009-10-07
Can’t you just comment out the offending lines in the sources.list?
gksu gedit /etc/apt/sources.list
Then change this:
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
to this:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
Save, and close

---

