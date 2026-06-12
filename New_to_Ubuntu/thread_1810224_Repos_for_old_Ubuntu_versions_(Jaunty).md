---
title: "Repos for old Ubuntu versions (Jaunty)"
date: 2011-07-22
forum: New to Ubuntu
---

### Post by pinefresh on 2011-07-22
Hi, I've been try to compile an old package that basically needs packages from around 2009 to compile properly. 

Debian Lenny's glibc package is too old while Ubuntu 10.04 LTS's x264 and ffmpeg packages are too new. Things just keep on breaking when trying to upgrade/downgrade packages.

So it seems like my only option is to find a repo for Jaunty. Does this exist? Thanks.

---

### Post by bkratz on 2011-07-22
> **pinefresh said:**
> Hi, I've been try to compile an old package that basically needs packages from around 2009 to compile properly. 

Debian Lenny's glibc package is too old while Ubuntu 10.04 LTS's x264 and ffmpeg packages are too new. Things just keep on breaking when trying to upgrade/downgrade packages.

So it seems like my only option is to find a repo for Jaunty. Does this exist? Thanks.

You will have to change your software sources to old-releases.... just like in this thread

[http://ubuntuforums.org/showthread.php?t=1190101](http://ubuntuforums.org/showthread.php?t=1190101)

---

### Post by wojox on 2011-07-22
You maybe able to find your packages here: [http://old-releases.ubuntu.com/ubuntu/pool/main/g/glibc/](http://old-releases.ubuntu.com/ubuntu/pool/main/g/glibc/)

---

### Post by pinefresh on 2011-07-23
Thanks for the replies.


It literally took me hours to download around 140mb from old-releases.ubuntu.com/. Then I installed something wrong and now have to do it all over again :popcorn:

My local Ubuntu mirrors don't have EOL releases in their ../ubuntu/dists folder but they all seem to have EOL files in their ../ubuntu/indices folder. Is there a way to access these mirrored files without the index files from ../ubuntu/dists available?

---

