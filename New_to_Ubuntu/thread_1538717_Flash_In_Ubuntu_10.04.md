---
title: "Flash In Ubuntu 10.04"
date: 2010-07-25
forum: New to Ubuntu
---

### Post by daniell59 on 2010-07-25
I am currently running Ubuntu 9.10 64 bit. After some difficulty I was able to install Adobe Flash. I was wondering whether Ubuntu 10.04 64 bit has flash installed. If not, will it be difficult to install it?

Thanks

---

### Post by cj.surrusco on 2010-07-25
It does not have it installed by default, but it can be done somewhat easily. You can only use the 32-bit version of flash, but it works fine on a 64-bit system.

There is info on that [here]("http://ubuntuforums.org/showthread.php?t=1491268").

---

### Post by eyeofreason on 2010-07-25
> **cj.surrusco said:**
> It does not have it installed by default, but it can be done somewhat easily. You can only use the 32-bit version of flash, but it works fine on a 64-bit system.

There is info on that [here]("http://ubuntuforums.org/showthread.php?t=1491268").

With all do respect I have never been able to get 32-bit flash or Java plug-ins to work with the 64-bit Ubuntu. However here is the sticky thak Killz was nice enough to compile into an easy to istall deb. 

[http://ubuntuforums.org/showthread.php?t=772490&highlight=killz+64+flash](http://ubuntuforums.org/showthread.php?t=772490&highlight=killz+64+flash)

be sure that you go to the end of the post since it has been updated as Flash has been updated.

---

### Post by cj.surrusco on 2010-07-25
> **eyeofreason said:**
> With all do respect I have never been able to get 32-bit flash or Java plug-ins to work with the 64-bit Ubuntu. However here is the sticky thak Killz was nice enough to compile into an easy to istall deb. 

[http://ubuntuforums.org/showthread.php?t=772490&highlight=killz+64+flash](http://ubuntuforums.org/showthread.php?t=772490&highlight=killz+64+flash)

be sure that you go to the end of the post since it has been updated as Flash has been updated.

I guess it works better for some people than others... ;)

---

### Post by marshmallow1304 on 2010-07-25
Adobe [recently pulled]("http://broadcast.oreilly.com/2010/06/running-64-bit-linux-no-flash.html") 64-bit Flash for Linux.  The latest 64-bit version they supplied has a serious security flaw.  It is strongly recommended that you use the 32-bit version available in the repository.  If you want to install the 64-bit version anyway, the [SevenMachines PPA]("https://launchpad.net/~sevenmachines/+archive/flash") has the latest version.

---

### Post by eyeofreason on 2010-07-25
I am running an older 64bit flash. Thanks for the heads up.  

It's been a year since i made the switch to 64bit so guess I'm my experience with it is outdated.

---

### Post by daniell59 on 2010-07-25
I don't remember which version I installed. How do I make that determination?
Thanks

---

### Post by eyeofreason on 2010-07-25
[http://www.adobe.com/software/flash/about/](http://www.adobe.com/software/flash/about/)

---

### Post by daniell59 on 2010-07-25
> **marshmallow1304 said:**
> Adobe [recently pulled]("http://broadcast.oreilly.com/2010/06/running-64-bit-linux-no-flash.html") 64-bit Flash for Linux.  The latest 64-bit version they supplied has a serious security flaw.  It is strongly recommended that you use the 32-bit version available in the repository.  If you want to install the 64-bit version anyway, the [SevenMachines PPA]("https://launchpad.net/~sevenmachines/+archive/flash") has the latest version.

How do I install the 32 bit in Ubuntu 10.04 64 bit?

Thanks

---

### Post by lovinglinux on 2010-07-25
> **daniell59 said:**
> How do I install the 32 bit in Ubuntu 10.04 64 bit?

Thanks

Get [FLASH-AID](http://flash-aid-extension.blogspot.com), an extension to remove conflicting flash plugins and install the proper version according to your browser architecture. Make sure you download version 1.0.9.

---

