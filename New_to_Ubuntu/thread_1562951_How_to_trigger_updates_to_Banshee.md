---
title: "How to trigger updates to Banshee"
date: 2010-08-28
forum: New to Ubuntu
---

### Post by robfuller on 2010-08-28
Hello,

I*have installed Banshee version 1.6.1 from the Ubuntu Software Center in Lucid. I'm trying to follow the instructions at [https://launchpad.net/~banshee-team/+archive/ppa](https://launchpad.net/~banshee-team/+archive/ppa) to add the Banshee team PPA so as to be able to update to the latest version, but having no luck.

I*have already gone to Systems >*Administration >*Software sources, and have added the PPA. On the Other Software tab, I*can see  "http://ppa.launchpad.net/banshee-team/ppa/ubuntu lucid main" listed as a source, and the box to the left is ticked. But when I*do sudo apt-get update, or when I*go through the Ubuntu Software Center, no updates to Banshee appear.

I've also tried uninstalling Banshee, but still the only version I*can find in the Software Center to reinstall from is as before - version 1.6.1.

Does anyone know what I'm doing wrong?

Thanks in advance,
Rob

---

### Post by Pollox on 2010-08-29
Banshee 1.6.1 is the latest version in that PPA right now.  If you want a newer version, use the unstable Banshee PPA (instructions are on the page you linked to) or compile it from source.

---

### Post by robfuller on 2010-08-29
Yes, but my problem is I*don't know how to use the Banshee PPA, as I*described...

---

### Post by Pollox on 2010-08-29
No, you're using *a* Banshee PPA just fine (specifically ppa:banshee-team/ppa).  That PPA does not have a newer version of Banshee.  You are mistaken in thinking that only seeing version 1.6.1 of Banshee indicates a problem.

If you want a newer version of Banshee than 1.6.1, you will need a different ppa (see [https://launchpad.net/~banshee-team/+archive/banshee-unstable](https://launchpad.net/~banshee-team/+archive/banshee-unstable)).

---

### Post by robfuller on 2010-08-29
Perfect! You're right, I*didn't understand that was the wrong PPA.
Thanks very much.

---

