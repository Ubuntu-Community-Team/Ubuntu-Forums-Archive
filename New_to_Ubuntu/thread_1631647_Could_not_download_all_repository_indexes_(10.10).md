---
title: "Could not download all repository indexes (10.10)"
date: 2010-11-26
forum: New to Ubuntu
---

### Post by utterness on 2010-11-26
I've only had Ubuntu for a little over 4 weeks now and I'm still adjusting to how things are run.  I've run into this error about 2 weeks ago, but I figured it wasn't that big of a deal since Ubuntu stopped informing me that it wasn't updating completely.  Now I've been trying to figure out another problem with my media player and I see the problem still exists and I can't do anything else to fix my most recent problem until my old one is solved.

~~~
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/warty/multiverse/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/warty/multiverse/source/Sources.gz)  404  Not Found [IP: 91.189.92.170 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/warty/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/warty/multiverse/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.92.170 80]
Failed to fetch [http://ppa.launchpad.net/exaile-devel/ppa/ubuntu/dists/maverick/main/source/Sources.gz](http://ppa.launchpad.net/exaile-devel/ppa/ubuntu/dists/maverick/main/source/Sources.gz)  404  Not Found
Failed to fetch [http://ppa.launchpad.net/exaile-devel/ppa/ubuntu/dists/maverick/main/binary-i386/Packages.gz](http://ppa.launchpad.net/exaile-devel/ppa/ubuntu/dists/maverick/main/binary-i386/Packages.gz)  404  Not Found
Some index files failed to download, they have been ignored, or old ones used instead.
~~~

I've tried a couple of suggestions thrown around the forums, but none of them worked.  And before I go and probably screw my system up, I thought I'd ask about my specific problem instead.

My internet connection is fine (I'm on here afterall).

thanks.

---

### Post by napoleon3665 on 2010-11-26
this means that the server that hosts the files no longer holds the files that you are trying to fetch, try another repository.

---

### Post by Foxheadz on 2010-11-26
Just delete the sources and find the correct ones

---

### Post by utterness on 2010-11-27
well, if it was that simple, then why did it seem to be such a high priority that one would solve this?

also is there some place I can find replacement repositories?  I really don't know where to look.

thanks.

---

### Post by Foxheadz on 2010-11-27
Well in your case it said 404 not found which means that the repo is no longer there. Maybe look were you originally found the source and see if there is an updated one

---

