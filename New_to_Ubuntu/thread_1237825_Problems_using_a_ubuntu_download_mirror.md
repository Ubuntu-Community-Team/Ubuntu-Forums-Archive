---
title: "Problems using a ubuntu download mirror"
date: 2009-08-11
forum: New to Ubuntu
---

### Post by Yvan300 on 2009-08-11
Ok, so i have decided to pick the option 'choose best serer' in the software sources menu. But when i let it reload i get the following errors.

Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

Failed to fetch [http://ftp.tuke.sk/ubuntu/dists/intrepid/main/binary-i386/Packages.gz](http://ftp.tuke.sk/ubuntu/dists/intrepid/main/binary-i386/Packages.gz)  302 Found
Failed to fetch [http://ftp.tuke.sk/ubuntu/dists/intrepid/restricted/binary-i386/Packages.gz](http://ftp.tuke.sk/ubuntu/dists/intrepid/restricted/binary-i386/Packages.gz)  302 Found
Failed to fetch [http://ftp.tuke.sk/ubuntu/dists/intrepid/main/source/Sources.gz](http://ftp.tuke.sk/ubuntu/dists/intrepid/main/source/Sources.gz)  302 Found
Failed to fetch [http://ftp.tuke.sk/ubuntu/dists/intrepid/restricted/source/Sources.gz](http://ftp.tuke.sk/ubuntu/dists/intrepid/restricted/source/Sources.gz)  302 Found
Failed to fetch [http://ftp.tuke.sk/ubuntu/dists/intrepid/universe/binary-i386/Packages.gz](http://ftp.tuke.sk/ubuntu/dists/intrepid/universe/binary-i386/Packages.gz)  302 Found
Failed to fetch [http://ftp.tuke.sk/ubuntu/dists/intrepid/universe/source/Sources.gz](http://ftp.tuke.sk/ubuntu/dists/intrepid/universe/source/Sources.gz)  302 Found
Failed to fetch [http://ftp.tuke.sk/ubuntu/dists/intrepid/multiverse/binary-i386/Packages.gz](http://ftp.tuke.sk/ubuntu/dists/intrepid/multiverse/binary-i386/Packages.gz)  302 Found
Failed to fetch [http://ftp.tuke.sk/ubuntu/dists/intrepid/multiverse/source/Sources.gz](http://ftp.tuke.sk/ubuntu/dists/intrepid/multiverse/source/Sources.gz)  302 Found
Failed to fetch [http://ftp.tuke.sk/ubuntu/dists/intrepid-updates/main/binary-i386/Packages.gz](http://ftp.tuke.sk/ubuntu/dists/intrepid-updates/main/binary-i386/Packages.gz)  302 Found
Failed to fetch [http://ftp.tuke.sk/ubuntu/dists/intrepid-updates/restricted/binary-i386/Packages.gz](http://ftp.tuke.sk/ubuntu/dists/intrepid-updates/restricted/binary-i386/Packages.gz)  302 Found
Failed to fetch [http://ftp.tuke.sk/ubuntu/dists/intrepid-updates/main/source/Sources.gz](http://ftp.tuke.sk/ubuntu/dists/intrepid-updates/main/source/Sources.gz)  302 Found
Failed to fetch [http://ftp.tuke.sk/ubuntu/dists/intrepid-updates/restricted/source/Sources.gz](http://ftp.tuke.sk/ubuntu/dists/intrepid-updates/restricted/source/Sources.gz)  302 Found
Failed to fetch [http://ftp.tuke.sk/ubuntu/dists/intrepid-updates/universe/binary-i386/Packages.gz](http://ftp.tuke.sk/ubuntu/dists/intrepid-updates/universe/binary-i386/Packages.gz)  302 Found
Failed to fetch [http://ftp.tuke.sk/ubuntu/dists/intrepid-updates/universe/source/Sources.gz](http://ftp.tuke.sk/ubuntu/dists/intrepid-updates/universe/source/Sources.gz)  302 Found
Failed to fetch [http://ftp.tuke.sk/ubuntu/dists/intrepid-updates/multiverse/binary-i386/Packages.gz](http://ftp.tuke.sk/ubuntu/dists/intrepid-updates/multiverse/binary-i386/Packages.gz)  302 Found
Failed to fetch [http://ftp.tuke.sk/ubuntu/dists/intrepid-updates/multiverse/source/Sources.gz](http://ftp.tuke.sk/ubuntu/dists/intrepid-updates/multiverse/source/Sources.gz)  302 Found
Failed to fetch [http://ftp.tuke.sk/ubuntu/dists/intrepid-security/main/binary-i386/Packages.gz](http://ftp.tuke.sk/ubuntu/dists/intrepid-security/main/binary-i386/Packages.gz)  302 Found
Failed to fetch [http://ftp.tuke.sk/ubuntu/dists/intrepid-security/restricted/binary-i386/Packages.gz](http://ftp.tuke.sk/ubuntu/dists/intrepid-security/restricted/binary-i386/Packages.gz)  302 Found
Failed to fetch [http://ftp.tuke.sk/ubuntu/dists/intrepid-security/main/source/Sources.gz](http://ftp.tuke.sk/ubuntu/dists/intrepid-security/main/source/Sources.gz)  302 Found
Failed to fetch [http://ftp.tuke.sk/ubuntu/dists/intrepid-security/restricted/source/Sources.gz](http://ftp.tuke.sk/ubuntu/dists/intrepid-security/restricted/source/Sources.gz)  302 Found
Failed to fetch [http://ftp.tuke.sk/ubuntu/dists/intrepid-security/universe/binary-i386/Packages.gz](http://ftp.tuke.sk/ubuntu/dists/intrepid-security/universe/binary-i386/Packages.gz)  302 Found
Failed to fetch [http://ftp.tuke.sk/ubuntu/dists/intrepid-security/universe/source/Sources.gz](http://ftp.tuke.sk/ubuntu/dists/intrepid-security/universe/source/Sources.gz)  302 Found
Failed to fetch [http://ftp.tuke.sk/ubuntu/dists/intrepid-security/multiverse/binary-i386/Packages.gz](http://ftp.tuke.sk/ubuntu/dists/intrepid-security/multiverse/binary-i386/Packages.gz)  302 Found
Failed to fetch [http://ftp.tuke.sk/ubuntu/dists/intrepid-security/multiverse/source/Sources.gz](http://ftp.tuke.sk/ubuntu/dists/intrepid-security/multiverse/source/Sources.gz)  302 Found
Some index files failed to download, they have been ignored, or old ones used instead.

What is the cause of this?

---

### Post by Yvan300 on 2009-08-11
Hey i think i should move this thread, seeing that it can't be easily answered. Could an admin please move it to networking or installation and upgrades. Maybe i'll find some luck there :)

---

### Post by overdrank on 2009-08-11
Hi and I am not familiar with > [http://ftp.tuke.sk/ubuntu/dists/intr...86/Packages.gz](http://ftp.tuke.sk/ubuntu/dists/intr...86/Packages.gz) 
Could you post your [source list]("https://help.ubuntu.com/community/Repositories/CommandLine")
```
 cat /etc/apt/sources.list

```

---

