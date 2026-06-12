---
title: "failed to update system"
date: 2010-02-06
forum: New to Ubuntu
---

### Post by medphys on 2010-02-06
Hi all,

Got this message this evening about updates that I had not seen before.

Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic/Release](http://us.archive.ubuntu.com/ubuntu/dists/karmic/Release)  Unable to find expected entry  main'./binary-amd64/Packages in Meta-index file (malformed Release file?)
Failed to fetch [http://winff.org/ubuntu/dists/Karmic/Koala/binary-amd64/Packages.gz](http://winff.org/ubuntu/dists/Karmic/Koala/binary-amd64/Packages.gz)  404  Not Found
Failed to fetch [http://winff.org/ubuntu/dists/Karmic/universe/binary-amd64/Packages.gz](http://winff.org/ubuntu/dists/Karmic/universe/binary-amd64/Packages.gz)  404  Not Found
Some index files failed to download, they have been ignored, or old ones used instead.

Does anybody know how to fix this so that I may download about 72 files that need upgrading?

Thanks for your help

---

### Post by quixote on 2010-02-07
Sometimes that just means there are bandwidth problems.  Have you tried it again to see if it works now?  

The following method hasn't usually made much difference for me, but it's also something you can try.  It's possible to change the download server: System > Software Sources : on first tab (Ubuntu software) click on the dropdown menu next to "Download Server".  Click on "other" to get the full list.  (If you have some time, you can have it scan for the fastest server for your location.)  It'll want to reload the entire repositories each time you select a new download server.

---

### Post by medphys on 2010-02-08
quixote,

Thanks for your reply, Tried that and still gave me the same results.  Been doing that for about 2 days now and said that I updated 22 days ago.  Know for a fact that I updated my kernel to 2.6.31.19 two days ago.  This is when all this happened. Also running 64 bit 9.1 Ubuntu.

Thanks

---

### Post by quixote on 2010-02-08
Hmm.  Since the problem includes different servers and keeps on going, maybe the problem is the interaction between the upgraded files and your router?  (Yeah, I'm just guessing.  Totally.)  Something like that I remembered happened to me once, and it went away after I rebooted my cablemodem / router.  

I doubt the problem is a bug in the upgrade because I think there'd be more reports of problems then.  Or maybe there are, and I just haven't seen them.  Have you checked bug reports on [launchpad]("https://bugs.launchpad.net/ubuntu/karmic")?

---

### Post by halitech on 2010-02-08
when I try to bring up the site this is what I get

[http://winff.org/ubuntu/dists/Karmic/universe/binary-amd64/](http://winff.org/ubuntu/dists/Karmic/universe/binary-amd64/)

Not Found

The requested URL /ubuntu/dists/Karmic/universe/binary-amd64/ was not found on this server.

Apache/2.2.9 (Debian) DAV/2 PHP/5.2.6-1+lenny4 with Suhosin-Patch proxy_html/3.0.0 mod_python/3.3.1 Python/2.5.2 mod_ssl/2.2.9 OpenSSL/0.9.8g mod_perl/2.0.4 Perl/v5.10.0 Server at winff.org Port 80

[http://us.archive.ubuntu.com/ubuntu/dists/karmic/Release](http://us.archive.ubuntu.com/ubuntu/dists/karmic/Release) - worked fine

---

### Post by medphys on 2010-02-08
That is exactly what I get.  Apache server cannot fond 64 bit packages.

---

### Post by quixote on 2010-02-08
The fact that halitech can't reach the winff server means it's nothing to do with your setup, upgrade, or system.  Their server is just plain down.  You should be able to use one of the bigger servers instead, unless it's a small repository that's only hosted there.

However, that can't be the case for *.ubuntu.com for days on end.  That's still a mystery....

---

### Post by halitech on 2010-02-08
can you post your sources.list file for us?

run this in the terminal
```
cat /etc/apt/sources.list
```

---

### Post by medphys on 2010-02-09
halitech

Here is the output of cat /etc/apt/sources.list

dan@dan-ubuntu-linux:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release amd64 (20091027)]/ karmic main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://mirror.umoss.org/ubuntu/](http://mirror.umoss.org/ubuntu/) karmic main restricted
deb-src [http://mirror.umoss.org/ubuntu/](http://mirror.umoss.org/ubuntu/) karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://mirror.umoss.org/ubuntu/](http://mirror.umoss.org/ubuntu/) karmic-updates restricted main main'.
deb-src [http://mirror.umoss.org/ubuntu/](http://mirror.umoss.org/ubuntu/) karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://mirror.umoss.org/ubuntu/](http://mirror.umoss.org/ubuntu/) karmic universe
deb-src [http://mirror.umoss.org/ubuntu/](http://mirror.umoss.org/ubuntu/) karmic universe
deb [http://mirror.umoss.org/ubuntu/](http://mirror.umoss.org/ubuntu/) karmic-updates universe
deb-src [http://mirror.umoss.org/ubuntu/](http://mirror.umoss.org/ubuntu/) karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://mirror.umoss.org/ubuntu/](http://mirror.umoss.org/ubuntu/) karmic multiverse
deb-src [http://mirror.umoss.org/ubuntu/](http://mirror.umoss.org/ubuntu/) karmic multiverse
deb [http://mirror.umoss.org/ubuntu/](http://mirror.umoss.org/ubuntu/) karmic-updates multiverse
deb-src [http://mirror.umoss.org/ubuntu/](http://mirror.umoss.org/ubuntu/) karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner

deb [http://mirror.umoss.org/ubuntu/](http://mirror.umoss.org/ubuntu/) karmic-security main restricted
deb-src [http://mirror.umoss.org/ubuntu/](http://mirror.umoss.org/ubuntu/) karmic-security main restricted
deb [http://mirror.umoss.org/ubuntu/](http://mirror.umoss.org/ubuntu/) karmic-security universe
deb-src [http://mirror.umoss.org/ubuntu/](http://mirror.umoss.org/ubuntu/) karmic-security universe
deb [http://mirror.umoss.org/ubuntu/](http://mirror.umoss.org/ubuntu/) karmic-security multiverse
deb-src [http://mirror.umoss.org/ubuntu/](http://mirror.umoss.org/ubuntu/) karmic-security multiverse
deb [http://mirror.umoss.org/ubuntu/](http://mirror.umoss.org/ubuntu/) karmic main'.
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) karmic-security restricted main multiverse main'. universe
dan@dan-ubuntu-linux:~$ 

Hope this helps?  I can access the sites now but cannot access the release or other packages .gz



untu/dists/karmic/Release  Unable to find expected entry  main'./binary-amd64/Packages in Meta-index file (malformed Release file?)
Failed to fetch [http://mirror.umoss.org/ubuntu/dists/karmic-updates/Release](http://mirror.umoss.org/ubuntu/dists/karmic-updates/Release)  Unable to find expected entry  main'./binary-amd64/Packages in Meta-index file (malformed Release file?)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/karmic-security/Release](http://security.ubuntu.com/ubuntu/dists/karmic-security/Release)  Unable to find expected entry  main'./binary-amd64/Packages in Meta-index file (malformed Release file?)
Failed to fetch [http://winff.org/ubuntu/dists/Karmic/Koala/binary-amd64/Packages.gz](http://winff.org/ubuntu/dists/Karmic/Koala/binary-amd64/Packages.gz)  404  Not Found


thanks for the help

---

### Post by quixote on 2010-02-10
I must be missing something because I don't see in your sources list why it's even going to "winff.org".  And try some other server instead of "umoss.org."  Just select "Main server" and see if it helps.  (System > Administration > Software Sources, and it's the long button next to "download from".)  ???

---

### Post by paul.gevers on 2010-02-12
> **quixote said:**
> The fact that halitech can't reach the winff server means it's nothing to do with your setup, upgrade, or system.  Their server is just plain down. 

No, it is not. It just means that the string is not correct. The correct string is  (without any koala thingy, and without capital letters)
```
deb http://winff.org/ubuntu karmic universe

```
and it is probably in /etc/apt/sources.list.d/winff.list, so please correct it.

---

