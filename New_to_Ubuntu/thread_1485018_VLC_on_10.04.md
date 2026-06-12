---
title: "VLC on 10.04"
date: 2010-05-16
forum: New to Ubuntu
---

### Post by Sup3r3g0 on 2010-05-16
How do I add the nightly builds of VLC to the repository? 

This is what VLC has, but it's for Intrepid Ibex.
[http://nightlies.videolan.org/](http://nightlies.videolan.org/)
```
Debian and Ubuntu repositiories

For Debian Sid I386 (unstable) add the following line to your sources.list:

deb http://nightlies.videolan.org/build/sid-i386/arch ./

For Debian Sid AMD64 (unstable) add the following line to your sources.list:

deb http://nightlies.videolan.org/build/sid-amd64/arch ./

For Ubuntu Intrepid I386 (unstable) add the following line to your sources.list:

deb http://nightlies.videolan.org/build/intrepid-i386/arch ./

For Ubuntu Intrepid AMD64 (unstable) add the following line to your sources.list:

deb http://nightlies.videolan.org/build/intrepid-amd64/arch ./


Those repositories contain a vlc-dbg package that you can install so you can run gdb to provide usefull backtrace when reporting bugs.
```

Will it still work? If not, is there another way to get the latest VLC available?

---

### Post by Sup3r3g0 on 2010-05-16
bump

---

### Post by Excedio on 2010-05-16
> **Sup3r3g0 said:**
> bump
 
Careful bumping.
 
**Rule of Thumb:** 24 Hours
 
 
 
 
 
 
Are you 64bit or 32bit?

---

### Post by Sup3r3g0 on 2010-05-16
Sorry, my bad.

---

### Post by Excedio on 2010-05-17
> **Excedio said:**
> Are you 64bit or 32bit?
 
Same question applies. :-)

---

### Post by Sup3r3g0 on 2010-05-17
Oh haha, sorry. I didn't see because it was at the bottom of the post. I have 32 bit. 

How difficult is it to compile it from source? Will I have to do anything extra I already have an older version of vlc installed?

---

