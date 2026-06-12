---
title: "Fiesty repositories not found"
date: 2009-02-28
forum: New to Ubuntu
---

### Post by arvevans on 2009-02-28
My 8.10 Ubuntu with Gnome recently began complaining about non-existing repositories for "fiesty" release.
[INDENT]Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty-backports/main/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty-backports/main/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty-backports/restricted/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty-backports/restricted/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty-backports/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty-backports/universe/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty-backports/multiverse/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty-backports/multiverse/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty-backports/main/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty-backports/main/source/Sources.gz)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty-backports/restricted/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty-backports/restricted/source/Sources.gz)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty-backports/universe/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty-backports/universe/source/Sources.gz)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty-backports/multiverse/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty-backports/multiverse/source/Sources.gz)  404 Not Found [IP: 91.189.88.46 80]
Some index files failed to download, they have been ignored, or old ones used instead.[/INDENT]

Is this serious, and what should I do about it?
_._

---

### Post by taurus on 2009-02-28
Yes, that is serious.  If you are running intrepid, there should not be any repo from feisty in /etc/apt/sources.list.  So, open a terminal and edit /etc/apt/sources.list

Applications -> Accessories -> Terminal
```
gksud gedit /etc/apt/sources.list
```
and remove all the repos with feisty in there.  Save it and then run

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by arvevans on 2009-03-01
Thanks.  The two fiesty backport entries in /etc/apt/sources.list have now been commented out.

Not sure how they got in there.  This computer was running fiesty earlier and was upgraded to intrepid when it was declared stable by using the on-line upgrade process.

For the past couple of weeks the "you have upgrades" flag has been appearing but clicking on it resulted in indications that the "system is up to date".  The next couple of days will tell if removing the fiesty backport links will also fix that problem.

Thanks again.

---

### Post by ptn107 on 2009-03-01
Support for Feisty Fawn ended in October 2008, so the archive is no longer hosted within the normal site.  If you plan on continuing to use Ubuntu 7.04 then you need to change your /etc/apt/sources.list accordingly (please remove all your current lines and replace them with these):

```
deb http://old-releases.ubuntu.com/ubuntu/ feisty main restricted universe multiverse
deb-src http://old-releases.ubuntu.com/ubuntu/ feisty main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ feisty-updates main restricted universe multiverse
deb-src http://old-releases.ubuntu.com/ubuntu/ feisty-updates main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
deb-src http://old-releases.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ feisty-security main restricted universe multiverse
deb-src http://old-releases.ubuntu.com/ubuntu/ feisty-security main restricted universe multiverse
```

You should consider an upgrade to at least 8.04.2 or 8.10.

---

### Post by arvevans on 2009-03-11
[INDENT] * ** ptn107** said: "You should consider an upgrade to at least 8.04.2 or 8.10."*[/INDENT]

I am running the latest upgrades in 8.10.  That is the crux of the problem.  These references to Fiesty just showed up a couple of weeks ago.

Apparently you didn't read the original post which clearly said I was running 8.10.

---

### Post by edo333 on 2009-04-17
Ironically I am running 7.04 and getting the error that needs the sourcelist update.  I am very thankful for the user who posted this fix even if he neglected to read your original post.  IT solved my problem.:D

---

