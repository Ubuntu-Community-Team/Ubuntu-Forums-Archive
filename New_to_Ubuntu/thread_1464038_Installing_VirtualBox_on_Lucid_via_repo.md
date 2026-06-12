---
title: "Installing VirtualBox on Lucid via repo"
date: 2010-04-27
forum: New to Ubuntu
---

### Post by CharlesA on 2010-04-27
Hi,

I am thinking about doing an install of Lucid on release day, but I was wondering anyone knows if there is already a repo set up for virtualbox for lucid, or if they'll create it later.

I've got it set up so the repo is added to my sources.list file and I am able to be updated and installed via apt-get instead of just straight dpkg.

I want to upgrade to Lucid, but want to make sure I'll be able to use VBox after the upgrade, without having to wait.

Hope that makes sense.

Thanks.

---

### Post by howefield on 2010-04-27
> **CharlesA said:**
> I was wondering anyone knows if there is already a repo set up for virtualbox for lucid, or if they'll create it later.

There isn't one set up yet, but I'd expect one to be available soon, probably not till some time after 29th.

---

### Post by bodhi.zazen on 2010-04-27
As an alternate to VirtualBox, assuming you have the hardware, consider migrating to KVM. KVM does not have all the features of Virtualbox, but it is easier to update.

---

### Post by CharlesA on 2010-04-27
Thanks for the info.

I might just keep karmic on the server until they have a repo set up for Lucid. Either that or just run it on a different machine.

---

### Post by Jive Turkey on 2010-04-27
I have added the karmic apt line to both a server and a desktop install of lucid beta 2 and both appear to be working just fine.

---

### Post by rpotter28 on 2010-04-27
> **Jive Turkey said:**
> I have added the karmic apt line to both a server and a desktop install of lucid beta 2 and both appear to be working just fine.

Is this the apt line you are talking about?

deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) lucid non-free

If so, it doesn't work.

Richard

---

### Post by CharlesA on 2010-04-27
Probably added it like for karmic:


deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) karmic non-free

---

### Post by Jive Turkey on 2010-04-27
> **rpotter28 said:**
> Is this the apt line you are talking about?

deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) lucid non-free

If so, it doesn't work.

Richard

Sorry, I wasn't very clear.  I have this line in sources.list```
deb http://download.virtualbox.org/virtualbox/debian karmic non-free

```
...and it works.

---

### Post by Jive Turkey on 2010-05-11
I just checked and found that the repo for lucid is up now.

---

### Post by CharlesA on 2010-05-11
> **Jive Turkey said:**
> I just checked and found that the repo for lucid is up now.

Awesome.

Thanks! :)

---

### Post by flyfishingphil on 2010-05-11
> **CharlesA said:**
> Hi,

I am thinking about doing an install of Lucid on release day, but I was wondering anyone knows if there is already a repo set up for virtualbox for lucid, or if they'll create it later.

I've got it set up so the repo is added to my sources.list file and I am able to be updated and installed via apt-get instead of just straight dpkg.

I want to upgrade to Lucid, but want to make sure I'll be able to use VBox after the upgrade, without having to wait.

Hope that makes sense.

Thanks.
check [http://download.virtualbox.org/debianlucid]("http://download.virtualbox.org/debianlucid")

I've installed it. It's the Sun Virtual Box. Haven't gotten it fully set yet but you can get more info at this [thread]("http://ubuntuforums.org/showthread.php?t=1474865") spydeyrch offers some great assist.

Hope this helps.

---

### Post by CharlesA on 2010-05-11
Just purged virtualbox-3.1 that I installed from the karmic repos and installed the one from the lucid repos. Not that it'll be much different, but better safe than sorry. :)

---

