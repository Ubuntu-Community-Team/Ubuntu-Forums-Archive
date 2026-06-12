---
title: "New to Ubuntu and need help"
date: 2009-01-21
forum: New to Ubuntu
---

### Post by joewx on 2009-01-21
Hello all,

I am new to Ubuntu.  I recently purchased a Dell Mini 9 with Ubuntu and upgraded the Ram to 2GB using a instructions from this forum.  

I was told that the Ubuntu version from Dell does not allow the Ubuntu to see and use the new expanded RAM.  What version of Ubuntu do I need, where can I find it, and will a new Ubuntu user like me have problems setting it up?

I also have some MS programs I'd like to use but I'm told I need Wine to do that.   Any help will be appreciated.

Thanks.

Joewx

---

### Post by D3M0L1$H3® on 2009-01-21
> **joewx said:**
> Hello all,

I am new to Ubuntu.  I recently purchased a Dell Mini 9 with Ubuntu and upgraded the Ram to 2GB using a instructions from this forum.  

I was told that the Ubuntu version from Dell does not allow the Ubuntu to see and use the new expanded RAM.  What version of Ubuntu do I need, where can I find it, and will a new Ubuntu user like me have problems setting it up?

I also have some MS programs I'd like to use but I'm told I need Wine to do that.   Any help will be appreciated.

Thanks.

Joewx
Most likely you should just upgrade to the newest, 8.10, Intrepid Ibex, just to be safe. A fresh install should most likely automatically detect the RAM, while preinstalled OSes are sometimes set to only read the hardware that was shipped with the software. 
As far as I can tell, Ubuntu 8.10 is the easiest and most user-friendly version to install thus far.
yes, installing wine will allow you to run many MS programs, but not all. You will need to (after you upgrade if ur doing so) ```
sudo apt-get update
sudo apt-get install wine

```
? i'm not sure, i use the synaptic package manager. make sure you tell it to use all availiable (all open source, community software, etc.)
and just install wine.
Then copy the ms installation to ur Ubuntu disk space, run it, it should automatically run in wine, if not right click and tell it to.
not all ms programs work perfectly in wine though, so be careful.
best of luck

---

### Post by Paqman on 2009-01-21
> **joewx said:**
> 
I was told that the Ubuntu version from Dell does not allow the Ubuntu to see and use the new expanded RAM.

You can check for yourself. I'm not familiar with the cut-down Ubuntu on the Mini-9, but if you can go to the System Monitor you should be able to see your current RAM.

Alternatively, if you can get to a terminal window then enter:
```
free -m
```
and look at the second line. It'll show the current used and installed RAM in megabytes.

---

### Post by Michael.Godawski on 2009-01-21
hi,

concerning the wine tool... have a look at the official website:
[http://www.winehq.org/](http://www.winehq.org/)

and for download and installation instructions here:
[http://www.winehq.org/download/deb](http://www.winehq.org/download/deb)

What MS software do you want to run in Ubuntu? Perhaps there are better supported substitutes.

---

### Post by D3M0L1$H3® on 2009-01-21
yes, often virtualbox or other emulation would be more appropriate depending on the software you wish to run.

---

### Post by Paqman on 2009-01-22
> **D3M0L1$H3® said:**
> yes, often virtualbox or other emulation would be more appropriate depending on the software you wish to run.

VMs aren't really an option on a netbook. They just don't have the system resources.

---

### Post by hyper_ch on 2009-01-22
It is advised to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question ;)

And it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

Or in short terms: Help others to help you ;)

Also, when you are asked to post output from (config) files or from a command, use [noparse]```

```[/noparse] brackets around (each) output. That makes it also easier to read.

---

