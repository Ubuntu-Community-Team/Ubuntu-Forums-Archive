---
title: "How to best REMOVE multiple duplicate sources of software?"
date: 2010-02-15
forum: New to Ubuntu
---

### Post by mikodo on 2010-02-15
Hello everyone,

I have multiple duplicate sources of software as seen in Software Sources > Other Software, and when I run sudo apt-get update. Is removing the duplicate sources in Software Sources > Other Software and exiting, a proper way to remove the duplicates? 

Or, is there a safer/correct way to do this?

Thank you.

See sceenshot below:

---

### Post by Temposs on 2010-02-15
That will work just fine.

---

### Post by Julita on 2010-02-15
I think you may want to edit the file /etc/apt/sources.list It contains all the sources, and you can edit it by running in a terminal sudo gedit /etc/apt/sources.list

---

### Post by mikodo on 2010-02-15
> **Julita said:**
> I think you may want to edit the file /etc/apt/sources.list It contains all the sources, and you can edit it by running in a terminal sudo gedit /etc/apt/sources.list

Yes, I have seen this mentioned before. So, what do I do with this:


# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic restricted main
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates restricted main
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-backports restricted universe multiverse main
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security restricted main
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) karmic free non-free
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-proposed restricted multiverse universe main
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) karmic non-free

---

### Post by howefield on 2010-02-15
> **mikodo said:**
> Yes, I have seen this mentioned before. So, what do I do with this:

You asked if there were a safer/correct way of doing it, there isn't. Your original post was spot on.

Editing the sources.list is easily done, but introduces an element of risk through typos or removing the wrong line.

---

### Post by mikodo on 2010-02-15
> **howefield said:**
> You asked if there were a safer/correct way of doing it, there isn't. Your original post was spot on.

Editing the sources.list is easily done, but introduces an element of risk through typos or removing the wrong line.

Sold: I'll take the original post way, being a newbie and ++ prone to mistakes!

Thank you everyone.

---

### Post by bodhi.zazen on 2010-02-15
> **Julita said:**
> I think you may want to edit the file /etc/apt/sources.list It contains all the sources, and you can edit it by running in a terminal sudo gedit /etc/apt/sources.list

I would advise you use gksu for graphical applications such as gedit.

---

### Post by mikodo on 2010-02-15
> **bodhi.zazen said:**
> I would advise you use gksu for graphical applications such as gedit.

Ah nuts....

I'm torn now as to what to do again. My first inclination is to do it a way, that is relatively free from newbie mistakes, but I hate to not follow the advice of a Ubuntu Forums Admin.

hmmm??

---

### Post by Temposs on 2010-02-15
he wasn't telling you which method to use. He was correcting the command to edit the sources.list file. If you were to edit the file manually, you would indeed want to use gksudo instead of sudo. But, that is not the safest method.

You should use the method you describe in your original post.

---

### Post by howefield on 2010-02-15
I don't think bodhi.zazen was advising what to do, merely correcting the advice of another poster.

---

### Post by mikodo on 2010-02-15
> **howefield said:**
> I don't think bodhi.zazen was advising what to do, merely correcting the advice of another poster.

Yes, I did see the difference in commands. You are probably correct.

Thank you.

Mike

---

### Post by mikodo on 2010-02-15
> **Temposs said:**
> he wasn't telling you which method to use. He was correcting the command to edit the sources.list file. If you were to edit the file manually, you would indeed want to use gksudo instead of sudo. But, that is not the safest method.

You should use the method you describe in your original post.

Thanks. I've worried this to death. bodhi.zazen was correct in telling me to use gksudo with Graphical Applications. 

Back to solved and using the Software Sources way.

Thank you everyone.

---

### Post by bodhi.zazen on 2010-02-15
Sorry for the confusion. There are multiple ways to "solve" the "problem" of "multiple duplicate sources", use any method you wish.

My intention was to point out that IMO it is best to use sudo for command line applications such as apt-get or nano, and gksu for graphical applications such as gedit or gvim.

If you want to know my personal preference, it is to use (with tab completion to reduce typos):

```
sudo -e /etc/apt/sources.list
``` and manually fix the problem. Of course keep in mind that is probably not the best method for new users and it is not "better" than other options.

---

