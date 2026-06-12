---
title: "resolving archives"
date: 2009-11-09
forum: New to Ubuntu
---

### Post by gwilkins82 on 2009-11-09
ok, been running 9.10 for a bit - more or less hassle free.  the past week or so ive had a red triangle telling me that my update info is outdated.  i ran a manual check of the updates to see what was going on.  i was missing some keys, so i went ahead and added those no problem.  i still have a few archives that cannot be resolved.  here are the errors:

W: Failed to fetch [http://archive/ubuntu.com/dists/karmic/Release.gpg](http://archive/ubuntu.com/dists/karmic/Release.gpg)  Could not resolve 'archive'

W: Failed to fetch [http://archive/ubuntu.com/dists/karmic/main/i18n/Translation-en_US.bz2](http://archive/ubuntu.com/dists/karmic/main/i18n/Translation-en_US.bz2)  Could not resolve 'archive'

W: Failed to fetch [http://archive/ubuntu.com/dists/karmic/universe/i18n/Translation-en_US.bz2](http://archive/ubuntu.com/dists/karmic/universe/i18n/Translation-en_US.bz2)  Could not resolve 'archive'

W: Failed to fetch [http://ppa.launchpad.net/jre-phoenix/ppf/ubuntu/dists/karmic/main/source/Sources.gz](http://ppa.launchpad.net/jre-phoenix/ppf/ubuntu/dists/karmic/main/source/Sources.gz)  404  Not Found

W: Some index files failed to download, they have been ignored, or old ones used instead.

what is my next move?

thanks all

---

### Post by diesch on 2009-11-09
In your software sources replace
```
[http://archive/ubuntu.com]("http://archive/ubuntu.com/dists/karmic/Release.gpg")
```
with 
```
[http://archive.ubuntu.com]("http://archive/ubuntu.com/dists/karmic/Release.gpg")
``` and

```
http://ppa.launchpad.net/jre-phoenix/ppf/
```
with
```
http://ppa.launchpad.net/jre-phoenix/ppa/
```

---

### Post by gwilkins82 on 2009-11-09
yikes.  couple of careless typos in there.  thanks!  ok, so that leaves me with these last two:

Failed to fetch [http://archive.ubuntu.com/dists/karmic/main/binary-i386/Packages.gz](http://archive.ubuntu.com/dists/karmic/main/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.88.135 80]
Failed to fetch [http://archive.ubuntu.com/dists/karmic/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/dists/karmic/universe/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.88.135 80]
Some index files failed to download, they have been ignored, or old ones used instead.

---

