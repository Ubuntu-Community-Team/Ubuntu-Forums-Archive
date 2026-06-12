---
title: "Update and Installation from ubuntu repository not possible"
date: 2010-05-01
forum: New to Ubuntu
---

### Post by PraveenP on 2010-05-01
I cannot update or install new software from official repositories, I haven't tried any other repositories. I just Installed a lucid (Lucid fresh install)

Command line output is here

one@oneslap:~$ sudo apt-get install gparted --fix-missing
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libparted0
Suggested packages:
  xfsprogs reiserfsprogs reiser4progs jfsutils kpartx dmraid
The following NEW packages will be installed:
  gparted libparted0
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 109kB/576kB of archives.
After this operation, 4,469kB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  libparted0 gparted
Install these packages without verification [y/N]? y
Err [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid/main libparted0 2.2-5ubuntu5
  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/p/parted/libparted0_2.2-5ubuntu5_amd64.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/p/parted/libparted0_2.2-5ubuntu5_amd64.deb)  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)

---

### Post by arpanaut on 2010-05-01
How long has this been going on?

I had that happen yesterday, I waited a while and all was good later.

Remember that the servers are under heavy load in the days shortly after new releases.

---

### Post by PraveenP on 2010-05-01
From today morning, 9 O clock IST. Still remains :(

---

### Post by r_vigneswaran on 2010-05-03
Please check whether the solution provided [here]("http://ubuntuforums.org/showthread.php?t=1466944") fits you.

---

