---
title: "trying to make a live cd of my own ubuntu distro"
date: 2009-12-14
forum: New to Ubuntu
---

### Post by Thocrun on 2009-12-14
I am following this guide:

[http://ubuntuforums.org/showthread.php?t=688872](http://ubuntuforums.org/showthread.php?t=688872)

but when I get to this 

Quote:
Note: For both gutsy and hardy you need to install extra package called [COLOR=Red]linux-ubuntu-modules-$(uname -r)[/COLOR]
Code:
sudo apt-get install [COLOR=Red]linux-ubuntu-modules-$(uname -r)[/COLOR]
This is not required for versions before gutsy, or version after hardy

the terminal says : E: Couldn't find package linux-ubuntu-modules-2.6.31-14-generic

---

### Post by yeats on 2009-12-14
> Quote:
Note: For both gutsy and hardy you need to install extra package called linux-ubuntu-modules-$(uname -r)
Code:
sudo apt-get install linux-ubuntu-modules-$(uname -r)
**This is not required for versions before gutsy, or version after hardy**

the terminal says : E: Couldn't find package linux-ubuntu-modules-2.6.31-14-generic

So what version are you running?  (If gutsy, you will want to upgrade to at least hardy).  If neither, then I would imagine the sentence I bolded will explain your issue :-).

---

### Post by sgosnell on 2009-12-14
Try it the easy way, with remastersys.  Download and install remastersys, and you can easily make your own live CD, as well as do complete backups and more.

---

### Post by k3lt01 on 2009-12-14
> **chrissharp123 said:**
> So what version are you running?  (If gutsy, you will want to upgrade to at least hardy).  If neither, then I would imagine the sentence I bolded will explain your issue :-).+1

Furthermore Gutsy isn't supported anymore so making your own distribution based on it would be futile.

---

