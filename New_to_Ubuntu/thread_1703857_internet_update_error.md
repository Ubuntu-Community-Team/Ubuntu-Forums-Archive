---
title: "internet update error"
date: 2011-03-09
forum: New to Ubuntu
---

### Post by go2xraj on 2011-03-09
W:GPG error: [http://www.sourceslist.eu](http://www.sourceslist.eu) lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 536D7B78FA088BA5, W:GPG error: [http://ubuntu.compiz.net](http://ubuntu.compiz.net) dapper Release: The following signatures were invalid: NODATA 1 NODATA 2, W:Failed to fetch [http://www.beerorkid.com/compiz/dists/dapper/main/binary-i386/Packages.gz](http://www.beerorkid.com/compiz/dists/dapper/main/binary-i386/Packages.gz)  404  Not Found
, W:Failed to fetch [http://ubuntu.compiz.net/dists/dapper/main/binary-i386/Packages.bz2](http://ubuntu.compiz.net/dists/dapper/main/binary-i386/Packages.bz2)  Sub-process /bin/bzip2 returned an error code (2)
, E:Some index files failed to download, they have been ignored, or old ones used instead.


This is the error please help me

---

### Post by PunkLV on 2011-03-09
Judging from your previous threads:
Go to [http://repogen.simplylinux.ch/](http://repogen.simplylinux.ch/)
Check the boxes you need, follow instructions

Or better yet:
```
cp /etc/apt/sources.list ~/.sources.list.old
sudo gedit /etc/apt/sources.list
```
Delete everything in it.
Paste this:
```

###### Ubuntu Main Repos
deb http://uk.archive.ubuntu.com/ubuntu/ maverick main restricted universe multiverse 
deb-src http://uk.archive.ubuntu.com/ubuntu/ maverick main restricted universe multiverse 

###### Ubuntu Update Repos
deb http://uk.archive.ubuntu.com/ubuntu/ maverick-security main restricted universe multiverse 
deb http://uk.archive.ubuntu.com/ubuntu/ maverick-updates main restricted universe multiverse 
deb-src http://uk.archive.ubuntu.com/ubuntu/ maverick-security main restricted universe multiverse 
deb-src http://uk.archive.ubuntu.com/ubuntu/ maverick-updates main restricted universe multiverse 

###### Ubuntu Partner Repo
deb http://archive.canonical.com/ubuntu maverick partner
deb-src http://archive.canonical.com/ubuntu maverick partner

```
Run:
```
sudo apt-get update
sudo apt-get upgrade
```

---

