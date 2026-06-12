---
title: "Using .rpm Files"
date: 2009-07-26
forum: New to Ubuntu
---

### Post by Commisar Jimp on 2009-07-26
I'm trying to get flash to work, so I downloaded a file from the flash web site, but it came as a .rpm file, and mythbuntu doesn't have any programs that read it, what program do I need to install it?

---

### Post by wojox on 2009-07-26
You could alien to convert it. If you went to the adobe website you should download the .deb package. You might want to do that instead.

---

### Post by starcraft.man on 2009-07-26
Flash is in the repos. No need for installing from an RPM or even a deb (unless you've had some specific problem, then please list in a reply). The package in the repos is *flashplugin-installer* . If you want to install lots of other extras like video codecs and other useful packages, see the *ubuntu-restricted-extras* package. See sig for instructions on installation.

Much easier than converting the rpm.

---

### Post by Commisar Jimp on 2009-07-26
I installed both files then went to youtube, but it still wouldn't play videos, is it maybe JavaScript that I need, and if so what is the package called?

---

### Post by markharding557 on 2009-07-26
> sudo apt-get install ubuntu-resticted-extrasshould sort you out

---

### Post by Commisar Jimp on 2009-07-26
That was it, thanks guys.

---

