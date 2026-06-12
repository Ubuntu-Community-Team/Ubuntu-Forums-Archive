---
title: "download repos?"
date: 2010-05-19
forum: New to Ubuntu
---

### Post by zer010 on 2010-05-19
Is it possible to download the entire Ubuntu repositories so as to keep a personal offline archive? I'm sure the space required would be HUGE, but I was just wondering.  How much space might it take to hold those thousands of apps and dependencies?

---

### Post by apjone on 2010-05-19
Have a look at [http://www.howtoforge.com/local_debian_ubuntu_mirror](http://www.howtoforge.com/local_debian_ubuntu_mirror)

---

### Post by halitech on 2010-05-19
you can try something like this script:

```
wget http://id.archive.ubuntu.com/ubuntu/dists/breezy/main/binary-i386/Packages.gz -O - |zcat|sed 's/Installed-Size://'|grep Size|awk '/Size:/ {pkgsize+=$2} END {print "package size = "pkgsize" Bytes"}'
```

(taken from here - [http://xlylith.blogspot.com/2006/02/size-of-ubuntu-repository.html](http://xlylith.blogspot.com/2006/02/size-of-ubuntu-repository.html) )

change breezy to the distro you want to find out about.

---

### Post by ankspo71 on 2010-05-19
Hi,
"The Complete Ubuntu Software Repository. Includes the entire main, restricted, multiverse, and universe repositories -- over 32GB of software."
Borrowed from: [http://www.osdisc.com/cgi-bin/view.cgi/products/linux/ubuntu/repo.html](http://www.osdisc.com/cgi-bin/view.cgi/products/linux/ubuntu/repo.html) (a site that sells them)

Have a look at: [http://keryxproject.org/](http://keryxproject.org/) and [http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/) .These are two ways to create your own smaller personal repositories for offline computers.

PS> I personally just backup my /var/cache/apt/archives/ folder to a new location so I don't have to redownload packages (like after a reinstall of Ubuntu). If I wanted to, I can install every package with a single command too.
Hope this helps.

---

### Post by Paqman on 2010-05-19
> **zer010 said:**
> How much space might it take to hold those thousands of apps and dependencies?

One of the guys on the Ubuntu UK podcast set up his own mirror recently, and said it was about 60GB (presumably that's both 32- and 64-bit)

---

### Post by elliotn on 2010-05-19
try this link here [http://www.ubuntuforums.org/showthread.php?t=819396](http://www.ubuntuforums.org/showthread.php?t=819396)

---

### Post by zer010 on 2010-05-19
Major thanks everyone! 30GB - 60GB isn't too bad. I was thinking it was going to be a couple hundred Gigabytes! A dedicated external hard drive is quite feasable, especially if it could be automatically updated from time to time. Thanks again!

---

