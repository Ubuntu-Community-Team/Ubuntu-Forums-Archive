---
title: "Why can't I install the new Open Office version?"
date: 2009-05-08
forum: New to Ubuntu
---

### Post by ubnewbie2 on 2009-05-08
The Update manager opens and suggests a partial upgrade.  I try that, but it fails.

```
An unresolvable problem occurred while calculating the upgrade.

 This can be caused by:
 * Upgrading to a pre-release version of Ubuntu
 * Running the current pre-release version of Ubuntu
 * Unofficial software packages not provided by Ubuntu

This is most likely a transient problem, please try again later.
```

*I am running the real 8.10 release - no pre-release has ever been on my machine.  Yes, I probably have some "unofficial" packages.  Doesn't everybody?

Meanwhile, a new version of open office is listed in the main update window, but it is not ticked, and it won't let me tick it for installation.

---

### Post by _Purple_ on 2009-05-08
Go to System > Administration > Software Sources. Under updates tab, do you have Pre-released updates(intrepid proposed) ticked? Which version of Open Office are you trying to install?

---

### Post by toutanc on 2009-05-08
It's often temporary (as mentionned). Usually, it's fixed the next day with the mirrors update. 

Did it just happen or did it start a few days ago ?

---

### Post by pastalavista on 2009-05-08
Apt can't handle it because it isn't supported in the repositories yet. You can download it manually [here]("http://download.openoffice.org/"). It's packaged in a tar.gz file. You can find instructions to install it [here]("http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68"). It'd be best probably to uninstall the version you already have in synaptic first unless you want two versions installed. that could cause some confusion.

---

### Post by ubnewbie2 on 2009-05-08
> **_Purple_ said:**
> Go to System > Administration > Software Sources. Under updates tab, do you have Pre-released updates(intrepid proposed) ticked? 

No, only the first 2 are ticked.

> **_Purple_ said:**
> Which version of Open Office are you trying to install?


It just says
```
The list of changes is not yet available.

Please use http://launchpad.net/ubuntu/+source/openoffice.org/1:3.1.0~rc2-1ubuntu1~intrepid1/+changelog
until the changes become available or try again later.

```

and strangely, that page is "unavailable" - but from the name, I suppose it's 3.1.0~rc2 --- sounds like an odd thing to be installing?

---

### Post by 3rdalbum on 2009-05-08
It's not been fully uploaded yet, that's why you can't apply it.

---

### Post by ubnewbie2 on 2009-05-08
> **pastalavista said:**
> Apt can't handle it because it isn't supported in the repositories yet. You can download it manually [here]("http://download.openoffice.org/"). It's packaged in a tar.gz file. You can find instructions to install it [here]("http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68"). It'd be best probably to uninstall the version you already have in synaptic first unless you want two versions installed. that could cause some confusion.

But I have only installed it via updates as far as I can remember.  I am pretty sure it's been updated in the past too.

It's not that I really want the version, it's just that it's inserted itself in the update list that Ubuntu keeps suggesting - then it won't install!  Kind of frustrating...

---

### Post by ubnewbie2 on 2009-05-08
> **3rdalbum said:**
> It's not been fully uploaded yet, that's why you can't apply it.


Surely it shouldn't appear in the list until it is ready?

---

### Post by ubnewbie2 on 2009-05-08
> **toutanc said:**
> It's often temporary (as mentionned). Usually, it's fixed the next day with the mirrors update. 

Did it just happen or did it start a few days ago ?

Actually, there's others in the list just like Open Office - and that's Acroread and also something called python-uno.  Acroread appeared some days ago, I remember that for sure.

As for the partial upgrade, I have only tried that tonight for the first time.

---

### Post by 3rdalbum on 2009-05-08
> **ubnewbie2 said:**
> Surely it shouldn't appear in the list until it is ready?

I agree, but I think it's a limitation of how Apt currently works.

---

### Post by emeraldgirl08 on 2009-05-08
I was wondering the same thing. I am running Ibex and using Open Office 2.4. All I want to do is upgrade to 3.0. 

Are there a lot of known bugs in it or is it pretty stable? 

I don't have the new version in my update manager and my prereleased box is unticked. Isn't Open Office 3.0 beyond a pre-release?

---

