---
title: "GTK+ versions"
date: 2009-11-24
forum: New to Ubuntu
---

### Post by futureismo on 2009-11-24
I've posted this here as I'm still a beginner so I hope this is the right place.

On attempting to install Wireshark from a tarball when I run the command
```
./configure
```I get the results (after a long series of successful checks):
```
checking for GTK+ - version >= 2.4.0... no
*** Could not run GTK+ test program, checking why...
*** The test program failed to compile or link. See the file config.log for the
*** exact error that occured. This usually means GTK+ is incorrectly installed.
configure: error: GTK+ 2.4 or later isn't available, so Wireshark can't be compiled

```I have GTK+ 2.18.3 installed, the latest release. And when I look on the GTK+ website versions 2.4, 2.6 and 2.8 are under "older versions" having been released around 2004!

Essentially: 
How does GTK+ name its releases? Why is 2.8 an older release than 2.18?
Is this the issue, how can I install Wireshark?
Thanks.

---

### Post by ankspo71 on 2009-11-24
Hi,
I have noticed this same naming technique for various programs on the web, and to be honest, it really bugs me. If gtk is the same way, then 2.8 is older than 2.18 because it is the 8th version of 2.0, and 2.18 is the 18th version. In my opinion, files should be labeled as 2.0* so that the majority of people will be able to distinguish the right files to get, or bump the version up a notch to 3.*. I suppose this is why most developers tend to date their file downloads... to eliminate some of the confusion.

As far as wireshark goes, I don't know, sorry.
James.

---

### Post by futureismo on 2009-11-24
> **ankspo71 said:**
> I have noticed this same naming technique for various programs on the web, and to be honest, it really bugs me. If gtk is the same way, then 2.8 is older than 2.18 because it is the 8th version of 2.0, and 2.18 is the 18th version.
Ah that makes a little more sense now, thank you. I also agree that naming would surely make sense if it followed the simple rule that the greater release number were the newer ones though, totally confused me at first. And hopefully someone here will find a solution for Wireshark. 
Cheers again.

---

### Post by ikt on 2009-11-24
why not grab wireshark from the repos?

---

### Post by futureismo on 2009-11-24
> **ikt said:**
> why not grab wireshark from the repos?
This is the reason I post in Absolute Beginners! I for some reason thought I had already attempted to install it using aptitude and that it wasn't in the repos. I wanted to give it a go installing from source anyway but thanks very much for this. I can only blame tiredness for not double checking. I'll mark the thread as solved.
Cheers for the help all.

---

