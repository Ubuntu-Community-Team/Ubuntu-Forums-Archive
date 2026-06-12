---
title: "Cannot get updates"
date: 2009-01-19
forum: New to Ubuntu
---

### Post by mramsey on 2009-01-19
I had to reload Edgy 6.10 on my sons comp. When I run the updates I get this message:

```
Authentication failed

Authenticating the upgrade failed. There may be a problem with the network or with the server.
``` 

I also get this when I try to add software

```
http://archive.ubuntu.com/ubuntu/dists/edgy-updates/main/binary-i386/Packages.gz: 404 Not Found [IP: 91.189.88.31 80]
http://security.ubuntu.com/ubuntu/dists/edgy-security/main/binary-i386/Packages.gz: 404 Not Found
http://archive.ubuntu.com/ubuntu/dists/edgy-updates/multiverse/binary-i386/Packages.gz: 404 Not Found [IP: 91.189.88.31 80]
http://archive.ubuntu.com/ubuntu/dists/edgy-updates/universe/binary-i386/Packages.gz: 404 Not Found [IP: 91.189.88.31 80]
http://security.ubuntu.com/ubuntu/dists/edgy-security/multiverse/binary-i386/Packages.gz: 404 Not Found
http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/binary-i386/Packages.gz: 404 Not Found
http://security.ubuntu.com/ubuntu/dists/edgy-security/main/source/Sources.gz: 404 Not Found
http://security.ubuntu.com/ubuntu/dists/edgy-security/multiverse/source/Sources.gz: 404 Not Found
http://security.ubuntu.com/ubuntu/dists/edgy-security/main/binary-i386/Packages.gz: 404 Not Found
http://archive.ubuntu.com/ubuntu/dists/edgy-updates/main/source/Sources.gz: 404 Not Found [IP: 91.189.88.31 80]
http://security.ubuntu.com/ubuntu/dists/edgy-security/multiverse/binary-i386/Packages.gz: 404 Not Found
http://security.ubuntu.com/ubuntu/dists/edgy-security/universe/binary-i386/Packages.gz: 404 Not Found
http://security.ubuntu.com/ubuntu/dists/edgy-security/main/source/Sources.gz: 404 Not Found
http://security.ubuntu.com/ubuntu/dists/edgy-security/multiverse/source/Sources.gz: 404 Not Found
http://security.ubuntu.com/ubuntu/dists/edgy-security/universe/source/Sources.gz: 404 Not Found
http://archive.ubuntu.com/ubuntu/dists/edgy-updates/multiverse/source/Sources.gz: 404 Not Found [IP: 91.189.88.31 80]
http://archive.ubuntu.com/ubuntu/dists/edgy-updates/universe/source/Sources.gz: 404 Not Found [IP: 91.189.88.31 80]
http://us.archive.ubuntu.com/ubuntu/dists/edgy/main/binary-i386/Packages.gz: 404 Not Found [IP: 91.189.88.45 80]
http://us.archive.ubuntu.com/ubuntu/dists/edgy/multiverse/binary-i386/Packages.gz: 404 Not Found [IP: 91.189.88.45 80]
http://us.archive.ubuntu.com/ubuntu/dists/edgy/restricted/binary-i386/Packages.gz: 404 Not Found [IP: 91.189.88.45 80]
http://us.archive.ubuntu.com/ubuntu/dists/edgy/main/source/Sources.gz: 404 Not Found [IP: 91.189.88.45 80]
http://us.archive.ubuntu.com/ubuntu/dists/edgy/multiverse/source/Sources.gz: 404 Not Found [IP: 91.189.88.45 80]
http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/source/Sources.gz: 404 Not Found [IP: 91.189.88.45 80]
http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz: 404 Not Found [IP: 91.189.88.45 80]
http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/main/binary-i386/Packages.gz: 404 Not Found [IP: 91.189.88.45 80]
http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/multiverse/binary-i386/Packages.gz: 404 Not Found [IP: 91.189.88.45 80]
http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/binary-i386/Packages.gz: 404 Not Found [IP: 91.189.88.45 80]
http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/main/source/Sources.gz: 404 Not Found [IP: 91.189.88.45 80]
http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/multiverse/source/Sources.gz: 404 Not Found [IP: 91.189.88.45 80]

```

Iam a little rusty at Ubuntu  please refresh my memory as to what I need to do. :confused:

---

### Post by Terl on 2009-01-19
Is there a reason you are using such an old version?  The current long term release is 8.04 and the latest release is 8.10.  You are getting the meesages you are because support has been dropped, I believe.  I would recommend you download a newer version of Ubuntu.

---

### Post by J03y on 2009-01-19
Yea I had the same problem like many months ago. I managed to upgrade 6.10 to 7.04. I think u had to open up a terminal and type sudo gedit /etc/apt/sources.list and then change all the words that say edgy to feisty then save it and then type sudo apt-get update. After that type sudo apt-get dist-upgrade.

---

### Post by mramsey on 2009-01-19
Long story short... I was having real problems trying to do a new install of 8.04 even from an original Canonical disk. It would go through the entire install and I could get the Login screen, enter user and password then just get a black screen and nothing else. I was getting a simillar issue when installing 7.04, 6.10 installed fine and is running so I was going to try installing through the updater.

---

### Post by Terl on 2009-01-19
You would not want to try upgrading through the updater through multiple versions anyway.  You may wish to try using the alternate install of one of the newer versions.  I am curious have you tried starting the newer version you have on disk in safe graphics mode?

What are the specs of the pc you are installing this on?

---

