---
title: "Virtual Box - newbie install mystery."
date: 2008-12-28
forum: New to Ubuntu
---

### Post by Orographic on 2008-12-28
Hi all,

I installed VB in Intrepid first by using this link below but had nothing but troubles with the system going into kernel panic (is that the term?) and not shutting down properly etc. I re-imaged via Acronis three times to an earlier state but still couldn't install VB without major shutdown probs.

[http://ubuntuforums.org/showpost.php?p=6393900&postcount=1](http://ubuntuforums.org/showpost.php?p=6393900&postcount=1)


Then I used this link instead and all seems well, with no shutdown issues thus far:

[http://www.ubuntugeek.com/how-to-install-virtualbox-21-in-ubuntu-810-intrepid-ibex804-hardy-heron.html](http://www.ubuntugeek.com/how-to-install-virtualbox-21-in-ubuntu-810-intrepid-ibex804-hardy-heron.html)

I'm trying to understand the difference in these two approaches. What does installing the public key do, via the second link? And did my actual installing of dkms actually help my system from not going into kernel panic?

I also had a warning when installing VB via both of those links that the installer was unable to find a precompiled module for the current kernel and did I want to select ok to automatically set one up? Was it okay to select okay in this instance?

Thanks all.

---

### Post by albinootje on 2008-12-28
> **Orographic said:**
> 
I'm trying to understand the difference in these two approaches. What does installing the public key do, via the second link? 

Those software packages were signed with an encryption key so that they can be trusted. You need to public key to verify that correctly.
Without the public key you can still install, but you will see a warning about "unauthenticated ...".
> 
And did my actual installing of dkms actually help my system from not going into kernel panic?

The package dkms is only to make sure that, after installing a new kernel, your kernel-modules needed for VirtualBox or nvidia video cards, will be available again.
> 
I also had a warning when installing VB via both of those links that the installer was unable to find a precompiled module for the current kernel and did I want to select ok to automatically set one up? Was it okay to select okay in this instance?

That's okay.No worries.

---

### Post by Orographic on 2008-12-28
Thanks mate, appreciate your time. Its a mystery then why my system wouldn't shutdown properly installing VB via the first link. Using the second link, all seems well.

---

