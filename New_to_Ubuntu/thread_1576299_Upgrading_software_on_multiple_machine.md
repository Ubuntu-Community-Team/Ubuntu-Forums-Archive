---
title: "Upgrading software on multiple machine"
date: 2010-09-17
forum: New to Ubuntu
---

### Post by ranjith19 on 2010-09-17
I have two machines running ubuntu 10.04 with identical softwares.
I keep upgrading softwares using apt-get update and upgrade. But my internet connection has an upper limit. I was wondering if it was possible to update my system by upgrading one of them and using the files in /var/cache/apt/archives?

---

### Post by Elfy on 2010-09-17
I've used apt-cacher-ng to do that - worked ok for me.

[http://ubuntuforums.org/showthread.php?t=981085](http://ubuntuforums.org/showthread.php?t=981085)

---

### Post by ajgreeny on 2010-09-17
Also **aptoncd** may be worth a look.  You don't even need to burn CDs, just use the iso files it makes.

---

### Post by Paqman on 2010-09-17
> **ranjith19 said:**
> I was wondering if it was possible to update my system by upgrading one of them and using the files in /var/cache/apt/archives?

Absolutely. Simply copying the packages from one machine to the other will work fine (you'll need to copy/paste with super user privileges, as the folder is owned by root). Note that both systems will need to be running the same architecture (ie: 32-bit or 64-bit). It'll save you re-downloading updates for all packages that on both systems, but obviously Update Manager will still need to download updates for packages that are unique to each machine. But if they're fairly similar then you should be able to cut your bandwidth use for updates by up to half.

If you want to automate the process you could also sync the two APT caches using a cron or anacron job.

---

### Post by ranjith19 on 2010-09-20
Thank you all. aptoncd worked really fine. damn, I didn't know about it.

UBUNTU ROCKS!

---

### Post by lbrty on 2010-09-20
This method works the fastest for me.

[http://ubuntuforums.org/showthread.php?t=819396](http://ubuntuforums.org/showthread.php?t=819396)

---

