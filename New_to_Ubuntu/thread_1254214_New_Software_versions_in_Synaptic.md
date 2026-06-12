---
title: "New Software versions in Synaptic"
date: 2009-08-31
forum: New to Ubuntu
---

### Post by yam.matt on 2009-08-31
Hello all,
         I am using Ubuntu Hardy Heron (8.04 LTS), my problem is that whenever I download software using the package mangers (synaptic or add/remove software) they download the older versions of software, I need to know how can I download the latest versions through them:confused:

---

### Post by nhasian on 2009-08-31
thats a good question.  for stability reasons you wont be able to upgrade to a newer version of a software package, only bugfix releases via the ubuntu repositories.

when you upgrade to a newer ubuntu you will get all the newer software packages.  for example Karmic Koala will come with firefox 3.5 by default.

of course you can always install the newer version of software applications yourself.  the easiest way is with PPAs, or deb packages.  what is it you would like to upgrade?

---

### Post by Perfect Storm on 2009-08-31
1. You can enable backports to get newer version. You might be in luck they have backported what you're looking for. Note that the backports are unsupported by Canonical/Ubuntu.

2. upgrade to the latest version of Ubuntu.

3. Check getdeb if they have a newer version available.

4. Compile from the Source.

---

### Post by kansasnoob on 2009-08-31
There are a few ways depending on the specific package. Sometimes you can find a trusted ppa on launchpad that will update specific packages, such as this (just an example):

[https://launchpad.net/~c-korn/+archive/ppa](https://launchpad.net/~c-korn/+archive/ppa)

You can also find individual packages by searching the package lists:

[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

You might find it in Hardy Backports:

[http://packages.ubuntu.com/hardy-backports/](http://packages.ubuntu.com/hardy-backports/)

Of course sometimes you can just search for a .deb or tar.gz.

---

### Post by colau on 2009-08-31
> **Artificial Intelligence said:**
> 1. You can enable backports to get newer version. You might be in luck they have backported what you're looking for. Note that the backports are unsupported by Canonical/Ubuntu.

2. upgrade to the latest version of Ubuntu.

3. Check getdeb if they have a newer version available.

4. Compile from the Source.
Why is backports not supported?

---

### Post by nhasian on 2009-08-31
> **colau said:**
> Why is backports not supported?

because it can potentially affect the stability of the system.  its a use at your own risk.  but from experience, i've never had any issues with it ^_^

---

### Post by yam.matt on 2009-08-31
Thanks for all your help guys:) Ill try to find a deb :)

---

