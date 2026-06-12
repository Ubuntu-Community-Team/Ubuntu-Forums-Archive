---
title: "Upgrading from 9.10 RC ?"
date: 2009-10-29
forum: New to Ubuntu
---

### Post by Loki57701 on 2009-10-29
How do I upgrade from the RC version to the final release? I tried:
```
sudo update-manager -d
```But it says my system is up to date.

---

### Post by novafluxx on 2009-10-29
> **Loki57701 said:**
> How do I upgrade from the RC version to the final release? I tried:
```
sudo update-manager -d
```But it says my system is up to date.

You already are on Final :-)

---

### Post by Loki57701 on 2009-10-29
How is that? I didn't download any updates.. was the RC identical to the final version?

---

### Post by winotree on 2009-10-29
Pretty much so.  If you downloaded available updates in the past few days then you're current.  Makes it easier that way I think.  ;)

---

### Post by Loki57701 on 2009-10-29
Sweet, thanks for the info guys.

---

### Post by mcduck on 2009-10-29
> **Loki57701 said:**
> How is that? I didn't download any updates.. was the RC identical to the final version?

Yes, that's pretty much the definition of RC.

RC version is released at the point when everything is ready. If there are no problems with the RC it's simply renamed to final. If any problems occur they are fixed and RC2 is released. Then if that has no problems it will be the final release, otherwise RC3 is released etc... So as long as everything seems to be OK with the RC version it is the same as final release. That's why it's called "Release Candidate". :)

And running "sudo update-manager -d" did nothing since you were already running 9.10, just like you were from the point t when you first installed the development version/Beta/RC. They are all one and the same release version.

---

### Post by dj-toonz on 2009-10-29
if you do this  lsb_release -a & it comes up with this

No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 9.10
Release:	9.10
Codename:	karmic


or in system, about Ubuntu you get this

You are using Ubuntu 9.10 - the Karmic Koala - released in October 2009 and supported until April 2011

Then your using the final release

---

