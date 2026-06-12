---
title: "System wont' upgrade"
date: 2010-08-08
forum: New to Ubuntu
---

### Post by jjohn1 on 2010-08-08
I have 8.4 on my system and I can't figure out how to upgrade to the 9, 9.4 10. whatever.  I clear my system today to get more room (I have a mini) ran my updates.  An upgrade is never available.  Here is what my screen says when I run "check" in update manager:

Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/restricted/binary-lpia/Packages.gz](http://security.ubuntu.com/ubuntu/dists/hardy-security/restricted/binary-lpia/Packages.gz)  404 Not Found [IP: 91.189.88.37 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/main/binary-lpia/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hardy/main/binary-lpia/Packages.gz)  404 Not Found [IP: 91.189.88.30 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/restricted/binary-lpia/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hardy/restricted/binary-lpia/Packages.gz)  404 Not Found [IP: 91.189.88.30 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/main/binary-lpia/Packages.gz](http://security.ubuntu.com/ubuntu/dists/hardy-security/main/binary-lpia/Packages.gz)  404 Not Found [IP: 91.189.88.37 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/binary-lpia/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/binary-lpia/Packages.gz)  404 Not Found [IP: 91.189.88.30 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-updates/main/binary-lpia/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hardy-updates/main/binary-lpia/Packages.gz)  404 Not Found [IP: 91.189.88.30 80]
Some index files failed to download, they have been ignored, or old ones used instead.


This has happened every time I try to upgrade.  Today I took the time to post to forum.  when I run update manager is says my system is up to date, but the package information was last update 561 days ago.  I have no idea what I'm doing

Thanks,

---

### Post by sandyd on 2010-08-08
> **jjohn1 said:**
> I have 8.4 on my system and I can't figure out how to upgrade to the 9, 9.4 10. whatever.  I clear my system today to get more room (I have a mini) ran my updates.  An upgrade is never available.  Here is what my screen says when I run "check" in update manager:

Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/restricted/binary-lpia/Packages.gz](http://security.ubuntu.com/ubuntu/dists/hardy-security/restricted/binary-lpia/Packages.gz)  404 Not Found [IP: 91.189.88.37 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/main/binary-lpia/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hardy/main/binary-lpia/Packages.gz)  404 Not Found [IP: 91.189.88.30 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/restricted/binary-lpia/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hardy/restricted/binary-lpia/Packages.gz)  404 Not Found [IP: 91.189.88.30 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/main/binary-lpia/Packages.gz](http://security.ubuntu.com/ubuntu/dists/hardy-security/main/binary-lpia/Packages.gz)  404 Not Found [IP: 91.189.88.37 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/binary-lpia/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/binary-lpia/Packages.gz)  404 Not Found [IP: 91.189.88.30 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-updates/main/binary-lpia/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hardy-updates/main/binary-lpia/Packages.gz)  404 Not Found [IP: 91.189.88.30 80]
Some index files failed to download, they have been ignored, or old ones used instead.


This has happened every time I try to upgrade.  Today I took the time to post to forum.  when I run update manager is says my system is up to date, but the package information was last update 561 days ago.  I have no idea what I'm doing

Thanks,
can you post the output of
```

cat /etc/apt/sources.list
```

and btw, lpia is no longer supported

---

### Post by snowpine on 2010-08-08
+1, there is no upgrade path for lpia. Back up your data and do a fresh install of 10.04 if you'd like the latest release.

8.04 will be supported until April 2011.

---

### Post by Jazzy_Jeff on 2010-08-08
Don't even mess with upgrading. Just back up your data as stated in other posts and do a clean install. A lot less problems down the line.

---

