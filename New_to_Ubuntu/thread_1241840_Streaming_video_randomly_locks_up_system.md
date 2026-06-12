---
title: "Streaming video randomly locks up system"
date: 2009-08-16
forum: New to Ubuntu
---

### Post by hifly1231 on 2009-08-16
When I first installed Ubuntu 8.10 on my computer, I never had this problem.  Then for a while it was both streaming video and streaming music that would completely lock up my system, and now it seems to only be streaming video.  When this happens, I have to manually turn off my computer and reboot.

Does this have something to do with the kernel (currently 2.6.27-14-generic) that I have installed?  How do I fix this problem?  Help!!!:confused:

I would really prefer not to have to do a fresh install!!!

---

### Post by nhasian on 2009-08-16
hello hifly1231,

we'll need more information to help you.  are you using 32 bit or 64 bit ubuntu?  is there any particular reason you stuck with 8.10 and didnt upgrade to 9.04?

what streaming problems are you having?  it is flash video like youtube?  can you post some example web sites so i can try to reproduce the problem?

can you please post the output of the terminal command:

```
apt-cache policy flashplugin-nonfree
```

---

### Post by hifly1231 on 2009-08-16
> **nhasian said:**
> hello hifly1231,

we'll need more information to help you.  are you using 32 bit or 64 bit ubuntu?  is there any particular reason you stuck with 8.10 and didnt upgrade to 9.04?

what streaming problems are you having?  it is flash video like youtube?  can you post some example web sites so i can try to reproduce the problem?

can you please post the output of the terminal command:

```
apt-cache policy flashplugin-nonfree
```

I'm using 32 bit Ubuntu 8.10.  I upgraded to 9.04 once, but my computer froze using it, and someone suggested that I go back to 8.10.

The problem is with websites such as YouTube.  I will want to watch a video, and sometimes I get all the way through it, and sometimes it will get stuck somewhere.  My entire system will freeze, and I will have to force shut-down (which I would NEVER do otherwise!!!).

Here is the output of the terminal command you gave me:

flashplugin-nonfree:
  Installed: 10.0.32.18ubuntu0.8.10.1
  Candidate: 10.0.32.18ubuntu0.8.10.1
  Version table:
 *** 10.0.32.18ubuntu0.8.10.1 0
        500 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/multiverse Packages
        500 [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Packages
        100 /var/lib/dpkg/status
     10.0.12.36ubuntu1 0
        500 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse Packages

Thanks for your help!!!

---

