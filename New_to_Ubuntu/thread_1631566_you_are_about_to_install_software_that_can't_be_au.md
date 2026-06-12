---
title: "you are about to install software that can't be authenticated"
date: 2010-11-26
forum: New to Ubuntu
---

### Post by noworldorder on 2010-11-26
Ubuntu 10.04 LTS

Recently the update manager says "you are about to install software that can't be authenticated"

This has never happened before. I did not update...

How do I figure out what is going on here?

Thx

---

### Post by s3MA00RRNY on 2010-11-26
If you add a repository you must also add its gpg key or you will get this error every time. Go to software sources and look at the last tab. Add your key there.

---

### Post by Xik on 2010-11-26
Refer to this thread:

[http://ubuntuforums.org/showthread.php?t=469280](http://ubuntuforums.org/showthread.php?t=469280)

Hope that works.

Xik.

---

### Post by noworldorder on 2010-11-27
> Refer to this thread:

[http://ubuntuforums.org/showthread.php?t=469280](http://ubuntuforums.org/showthread.php?t=469280)

Hope that works.

XikThanks but that didn't work for me.
> If you add a  repository you must also add its gpg key or you will get this error  every time. Go to software sources and look at the last tab. Add your  key there.[B]

I am not sure if or when or how I may have added a repository - how would I find out so I know what key to add


[/B]

---

### Post by muut on 2011-01-20
> **noworldorder said:**
> Thanks but that didn't work for me.
[B]

I am not sure if or when or how I may have added a repository - how would I find out so I know what key to add


[/B]

Have you been able to find an answer? I may be having a similar issue... posted at:

[http://ubuntuforums.org/showthread.php?t=1669307](http://ubuntuforums.org/showthread.php?t=1669307)

---

### Post by noworldorder on 2011-02-10
> Have you been able to find an answer? I may be having a similar issue... posted at:

[http://ubuntuforums.org/showthread.php?t=1669307](http://ubuntuforums.org/showthread.php?t=1669307)No luck.. I never figured it out. Since then (for other reasons) I did a fresh reinstall.  Good luck

---

### Post by mick222 on 2011-02-10
you must have installed a ppa maybe google chrome or something like that and not installed the gpg key. Try using Ubuntu tweak to reinstall the ppa or find and install the key lookin synaptic under origins to see what repositories you are using

---

### Post by WSmart on 2012-08-02
I just got this while trying to install pwsafe.   After I ran updates, the program installed without the warning.  I'm using apt-cacher and this was on a client machine.  Not sure that matters.  Good luck to anyone having this issue.  Try to run updates first.  Worked for me.

```
sudo apt-get update
sudo apt-get upgrade

```

---

### Post by ijumpship on 2012-08-03
Let Me give you a non-obvious answer (if there is such a word).network problem check that and just look at edit--->Source in your package manger or software center and see which source have no keys or the non conical/ubuntu sources

---

### Post by lisati on 2012-08-03
Old thread closed

---

