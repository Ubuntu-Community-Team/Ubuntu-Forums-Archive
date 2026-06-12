---
title: "Stuck with 8.10?"
date: 2010-11-10
forum: New to Ubuntu
---

### Post by BenDriscoll on 2010-11-10
Hey there, I've googled like mad to solve this problem, but to no avail.

I have a webserver running 8.10, 64 bit. I recently discovered that I can't apt-get anymore, and that intrepid is gone from archive.ubuntu.com

I'd like to upgrade to 10.04, but how do I do that? Can I even do that? I can't apt-get anything. I am a programmer by trade, but I don't know much about linux admin stuff. Normally I'd just wing it and find out the hard way, but this is my main web server, and I don't really want to mess it up.

Failing that, is there some backup of the 8.10 repositories?

Also: I've been told to just set up a new server with 10.04 LTS, but it's such a nightmare to migrate live web sites that I would consider it a last resort.

---

### Post by tad1073 on 2010-11-10
have you tried aptitude?

```
sudo aptitude package-name
```

---

### Post by BenDriscoll on 2010-11-10
I don't have aptitude, only apt-get.

When I run apt-get, I get pages of this:

```
W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/multiverse/source/Sources.gz  404 Not Found [IP: 91.189.88.45 80]
```

For all the sources in the list, as intrepid is no longer supported.

---

### Post by BenDriscoll on 2010-11-10
EDIT: I said I'd solved the problem, but I actually hadn't.

Does anyone know how I can upgrade to 10.04 from 8.10? I can't get update-manager-core to install with apt-get. Is there a workaround?

---

### Post by ubuntu27 on 2010-11-11
Check out:

[Upgrading End of Life releases]("https://help.ubuntu.com/community/EOLUpgradesvv")

Also:

[http://ubuntuforums.org/showpost.php?p=10101249&postcount=4](http://ubuntuforums.org/showpost.php?p=10101249&postcount=4)

---

### Post by uRock on 2010-11-11
From what I have read, you would have to go from 8.10 to 9.04 to 9.10, then to 10.04.

I would recommend backing up everything, then running a clean install of 10.04, so that you don't have to worry about upgrading again for a while.

---

### Post by mastablasta on 2010-11-11
also for server use it might be better to use **LTS** release and **server** release as they are supported for 5 years.

---

### Post by theozzlives on 2010-11-11
Everything from 9.04 and earlier is EOL. You may have to do your last resort and go to 10.04 LTS.

---

### Post by BenDriscoll on 2010-11-11
Yeah, I tried a bunch of stuff but it got messy. So instead I just started a new server with 10.04 and migrated my databases and files. Took a couple hours, but at least now I have peace of mind that I haven't messed something up horribly.

---

### Post by theozzlives on 2010-11-11
> **BenDriscoll said:**
> Yeah, I tried a bunch of stuff but it got messy. So instead I just started a new server with 10.04 and migrated my databases and files. Took a couple hours, but at least now I have peace of mind that I haven't messed something up horribly.

And you're good for five years!

---

### Post by ibizatunes on 2010-11-11
backup and clean build of 10:04 LTS > will save you hours of time compared to updating to 9:04 then 9:10 then 10:04

---

### Post by BenDriscoll on 2010-11-11
> **theozzlives said:**
> And you're good for five years!

Five years! By 2015 we'll all probably be energy based life forms living on a planet made of crystal. So I'm not worried about upgrading Ubuntu again.

---

