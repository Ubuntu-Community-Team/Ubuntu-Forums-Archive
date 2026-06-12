---
title: "Update manager error"
date: 2009-05-20
forum: New to Ubuntu
---

### Post by aravindc26 on 2009-05-20
i use ubuntu 8.10.
when i click check in update manager i get the following error.

```
Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

Failed to fetch http://archive.ubuntu.com/ubuntu/dists/warty/multiverse/binary-i386/Packages.gz  404 Not Found [IP: 91.189.88.46 80]
Some index files failed to download, they have been ignored, or old ones used instead.


```

how do i solve it

---

### Post by TransitMan on 2009-05-20
Open your sources.list file and either delete the reference to WARTY, which is no longer supported or place a # in front of [http://archive.ubuntu.com/ubuntu/dists/warty/multiverse](http://archive.ubuntu.com/ubuntu/dists/warty/multiverse)

---

### Post by aravindc26 on 2009-05-21
> **TransitMan said:**
> Open your sources.list file and either delete the reference to WARTY, which is no longer supported or place a # in front of [http://archive.ubuntu.com/ubuntu/dists/warty/multiverse](http://archive.ubuntu.com/ubuntu/dists/warty/multiverse)
Where is the file located ?

---

### Post by _Purple_ on 2009-05-21
You can open the file by typing the following command in terminal:
```
 gksudo gedit /etc/apt/sources.list

```

Then save it and type in terminal: 
```
sudo apt-get update
```

---

