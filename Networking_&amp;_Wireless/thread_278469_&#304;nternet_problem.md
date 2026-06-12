---
title: "&#304;nternet problem"
date: 2006-10-16
forum: Networking &amp; Wireless
---

### Post by chaoticnoise on 2006-10-16
Hi,
After hardly installing Ubuntu because of the Jmicron SATA controller now i am having different problems with network.The ethernet device is ok,i can also log in to the admin panel of the router,also with some changes on Firefox now i am also able to surf.But i cant log with Gaim,or the software update behaves like i have no internet connection?How can i fix that problem??

output of sudo apt-get update:
gn [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg
Ign [http://tr.archive.ubuntu.com](http://tr.archive.ubuntu.com) dapper Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Ign [http://tr.archive.ubuntu.com](http://tr.archive.ubuntu.com) dapper-updates Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Ign [http://tr.archive.ubuntu.com](http://tr.archive.ubuntu.com) dapper Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Ign [http://tr.archive.ubuntu.com](http://tr.archive.ubuntu.com) dapper-updates Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Ign [http://tr.archive.ubuntu.com](http://tr.archive.ubuntu.com) dapper/main Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
Ign [http://tr.archive.ubuntu.com](http://tr.archive.ubuntu.com) dapper/restricted Packages
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
404 Not Found
Ign [http://tr.archive.ubuntu.com](http://tr.archive.ubuntu.com) dapper/main Sources
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
404 Not Found
Ign [http://tr.archive.ubuntu.com](http://tr.archive.ubuntu.com) dapper/restricted Sources
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
404 Not Found
Ign [http://tr.archive.ubuntu.com](http://tr.archive.ubuntu.com) dapper-updates/main Packages
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
404 Not Found
Ign [http://tr.archive.ubuntu.com](http://tr.archive.ubuntu.com) dapper-updates/restricted Packages
Ign [http://tr.archive.ubuntu.com](http://tr.archive.ubuntu.com) dapper-updates/main Sources
Ign [http://tr.archive.ubuntu.com](http://tr.archive.ubuntu.com) dapper-updates/restricted Sources
Err [http://tr.archive.ubuntu.com](http://tr.archive.ubuntu.com) dapper/main Packages
404 Not Found
Err [http://tr.archive.ubuntu.com](http://tr.archive.ubuntu.com) dapper/restricted Packages
404 Not Found
Err [http://tr.archive.ubuntu.com](http://tr.archive.ubuntu.com) dapper/main Sources
404 Not Found
Err [http://tr.archive.ubuntu.com](http://tr.archive.ubuntu.com) dapper/restricted Sources
404 Not Found
Err [http://tr.archive.ubuntu.com](http://tr.archive.ubuntu.com) dapper-updates/main Packages
404 Not Found
Err [http://tr.archive.ubuntu.com](http://tr.archive.ubuntu.com) dapper-updates/restricted Packages
404 Not Found
Err [http://tr.archive.ubuntu.com](http://tr.archive.ubuntu.com) dapper-updates/main Sources
404 Not Found
Err [http://tr.archive.ubuntu.com](http://tr.archive.ubuntu.com) dapper-updates/restricted Sources
404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/di...86/Packages.gz](http://security.ubuntu.com/ubuntu/di...86/Packages.gz) 404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/di...86/Packages.gz](http://security.ubuntu.com/ubuntu/di...86/Packages.gz) 404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/di...rce/Sources.gz](http://security.ubuntu.com/ubuntu/di...rce/Sources.gz) 404 Not Found
Failed to fetch [http://tr.archive.ubuntu.com/ubuntu/...86/Packages.gz](http://tr.archive.ubuntu.com/ubuntu/...86/Packages.gz) 404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/di...rce/Sources.gz](http://security.ubuntu.com/ubuntu/di...rce/Sources.gz) 404 Not Found
Failed to fetch [http://tr.archive.ubuntu.com/ubuntu/...86/Packages.gz](http://tr.archive.ubuntu.com/ubuntu/...86/Packages.gz) 404 Not Found
Failed to fetch [http://tr.archive.ubuntu.com/ubuntu/...rce/Sources.gz](http://tr.archive.ubuntu.com/ubuntu/...rce/Sources.gz) 404 Not Found
Failed to fetch [http://tr.archive.ubuntu.com/ubuntu/...rce/Sources.gz](http://tr.archive.ubuntu.com/ubuntu/...rce/Sources.gz) 404 Not Found
Failed to fetch [http://tr.archive.ubuntu.com/ubuntu/...86/Packages.gz](http://tr.archive.ubuntu.com/ubuntu/...86/Packages.gz) 404 Not Found
Failed to fetch [http://tr.archive.ubuntu.com/ubuntu/...86/Packages.gz](http://tr.archive.ubuntu.com/ubuntu/...86/Packages.gz) 404 Not Found
Failed to fetch [http://tr.archive.ubuntu.com/ubuntu/...rce/Sources.gz](http://tr.archive.ubuntu.com/ubuntu/...rce/Sources.gz) 404 Not Found
Failed to fetch [http://tr.archive.ubuntu.com/ubuntu/...rce/Sources.gz](http://tr.archive.ubuntu.com/ubuntu/...rce/Sources.gz) 404 Not Found
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
chaotic@Chaotic-linux:~$
Edit/Delete Message

---

### Post by skymt on 2006-10-16
You have an error in your sources.list. Please run "cat /etc/apt/sources.list" in a terminal, and post the output, and I'll help you fix it.

---

### Post by handy on 2006-10-17
You may find that **_Option 3_**, of **_Post 13_**, in [this thread]("http://www.ubuntuforums.org/showthread.php?t=128254&page=2") will do it for you.

It works beautifuly for me.

---

### Post by skymt on 2006-10-17
> **handy said:**
> You may find that **_Option 3_**, of **_Post 13_**, in [this thread]("http://www.ubuntuforums.org/showthread.php?t=128254&page=2") will do it for you.

It works beautifuly for me.

It's not a nameserver issue, he has a bad sources.list.

---

### Post by chaoticnoise on 2006-10-17
Hi;
this is the output:

deb [http://tr.archive.ubuntu.com/ubuntu/](http://tr.archive.ubuntu.com/ubuntu/) dapper main restricted universe
deb-src [http://tr.archive.ubuntu.com/ubuntu/](http://tr.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://tr.archive.ubuntu.com/ubuntu/](http://tr.archive.ubuntu.com/ubuntu/) dapper-updates main restricted universe
deb-src [http://tr.archive.ubuntu.com/ubuntu/](http://tr.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://tr.archive.ubuntu.com/ubuntu/](http://tr.archive.ubuntu.com/ubuntu/) dapper universe
# deb-src [http://tr.archive.ubuntu.com/ubuntu/](http://tr.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://tr.archive.ubuntu.com/ubuntu/](http://tr.archive.ubuntu.com/ubuntu/) dapper-backports main restricted univ erse multiverse
# deb-src [http://tr.archive.ubuntu.com/ubuntu/](http://tr.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

---

### Post by skymt on 2006-10-17
Try using the universal servers. That would mean removing "tr." from each line. For example, "tr.archive.ubuntu.com" becomes "archive.ubuntu.com".

---

