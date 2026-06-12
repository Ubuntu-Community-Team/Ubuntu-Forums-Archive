---
title: "firefox upgrade question"
date: 2009-07-17
forum: New to Ubuntu
---

### Post by gwilkins82 on 2009-07-17
currently running firefox 3.0.11

no real problems, but saw that firefox 3.5 was out.  went to their site, downloaded the archive for linux 3.5.  i extracted the folder to my desktop, but have no idea what to do with it.  sorry - i'm sure this is a very stupid question, but what do i do to upgrade?

thanks

---

### Post by -=hazard=- on 2009-07-17
The one at firefox site is not the ubuntu release, I mean not testet by ubuntu, anyway just place the extracted folder on your home directory and run from there ./firefox, or simply create a link to it.

---

### Post by jerome1232 on 2009-07-17
If your running intrepid it's actually in the repo's as firefox-3.5

---

### Post by Tibuda on 2009-07-17
You can also check [this thread]("http://ubuntuforums.org/showthread.php?t=1193567"). It describes 4 ways to install the newest Firefox.

---

### Post by gwilkins82 on 2009-07-17
wow - thanks for all the insanely quick replies.  i didn't realize that it was not tested for ubuntu yet.  bummer.  i will just wait i think.

thanks a lot.

---

### Post by jerome1232 on 2009-07-17
> **jerome1232 said:**
> If your running intrepid it's actually in the repo's as firefox-3.5

^^^ version in the repos = tested

---

### Post by gwilkins82 on 2009-07-17
why do these methods install it under a different name and leave 3.0 still on the system as opposed to an upgrade?

---

### Post by Tibuda on 2009-07-17
> **gwilkins82 said:**
> why do these methods install it under a different name and leave 3.0 still on the system as opposed to an upgrade?

There's not an option to upgrade. The closest thing you can do is install the [firefox-3.5]("apt:firefox-3.5") package from the repositories, and uninstall the firefox package. You just have to know that firefox-3.5 is called Shiretoko instead of Firefox, but it is the same application.

Ubuntu is not a rolling release distro. All software that ubuntu supports is from the release date (april for jaunty). Only security updates are available from Canonical, not major releases like FF 3.5.

---

### Post by gwilkins82 on 2009-07-17
oh, ok.  not as complicated as i thought (although my question still seems idiotic)

thanks for the help!

---

### Post by Tibuda on 2009-07-17
> **gwilkins82 said:**
> oh, ok.  not as complicated as i thought (although my question still seems idiotic)

thanks for the help!

An idiot question is a question not asked! :)

---

### Post by Garyhans on 2009-07-17
It's Shiretoko. You can install it and keep the 3.0 version. Works great.

---

### Post by jerome1232 on 2009-07-17
> **gwilkins82 said:**
> why do these methods install it under a different name and leave 3.0 still on the system as opposed to an upgrade?

Probably because it is still in beta and some people might not like having their stable release replaced by a beta release.

---

### Post by Tibuda on 2009-07-17
> **jerome1232 said:**
> Probably because it is still in beta and some people might not like having their stable release replaced by a beta release.

It's not beta anymore.

---

### Post by -=hazard=- on 2009-07-17
> **danielrmt said:**
> It's not beta anymore.

It might be for Mozilla corp. but till Ubuntu test it and upgrade on repo, for us remains beta.

---

### Post by Tibuda on 2009-07-17
> **-=hazard=- said:**
> It might be for Mozilla corp. but till Ubuntu test it and upgrade on repo, for us remains beta.

No. It was a beta when jaunty was released. Now the firefox-3.5 package already have the final version. The default Ubuntu jaunty web browser will continue to be 3.0 forever, but 3.5 final is already available (branded as Shiretoko, don't be cheated by the name). The Ubuntu update manager will never ask you to upgrade from 3.0 to 3.5, because this is not a security update. You have to install manually the package [firefox-3.5]("apt:firefox-3.5"), uninstall firefox (or you can keep both if you want, that's why they keep the Shiretoko name) and [change your preferred browser]("http://www.ubuntugeek.com/select-preferred-applications-in-ubuntu.html") to firefox-3.5.

---

### Post by Garyhans on 2009-07-17
You don't have to uninstall you current 3.0

[http://compustorm.no-ip.org/2009/07/howto-install-firefox-3-5-on-ubuntu-jaunty/](http://compustorm.no-ip.org/2009/07/howto-install-firefox-3-5-on-ubuntu-jaunty/)

---

