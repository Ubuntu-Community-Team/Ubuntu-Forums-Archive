---
title: "could not mark all packages for installation"
date: 2011-02-07
forum: New to Ubuntu
---

### Post by kigali on 2011-02-07
Hi there,

I'm trying to install libx11-dev, I need it to install another thing. When I try to do it within synaptic I got this error:
Could not mark all packages for installation
libx11-dev:
 Depends: libxcb1-dev but it is not going to be installed

Within apt-get:
The following packages have unmet dependencies:
  libx11-dev: Depends: libxcb1-dev but it is not going to be installed
E: Broken packages

That's my version of ubuntu (jaunty):
uname -a
Linux pmslap 2.6.28-17-generic #58-Ubuntu SMP Tue Dec 1 18:57:07 UTC 2009 i686 GNU/Linux

Any clue what could I try? I already looked for similar threads in this forum but the hints didn't help me :/

---

### Post by Zill on 2011-02-07
> **kigali said:**
> ...That's my version of ubuntu (jaunty):
uname -a
Linux pmslap 2.6.28-17-generic #58-Ubuntu SMP Tue Dec 1 18:57:07 UTC 2009 i686 GNU/Linux...
Unfortunately, Jaunty (9.04) reached [end-of-life]("https://wiki.ubuntu.com/Releases") on October 23, 2010 and so is no longer supported.
I suggest you upgrade to a supported version such as 10.04 (Lucid) or 10.10 (Maverick).

---

### Post by kigali on 2011-02-07
> **Zill said:**
> Unfortunately, Jaunty (9.04) reached [end-of-life]("https://wiki.ubuntu.com/Releases")  on October 23, 2010 and so is no longer supported.
I suggest you upgrade to a supported version such as 10.04 (Lucid) or  10.10 (Maverick).


So that's the only reason? But I should be able to install some older version of x11lib, right?

---

### Post by oldos2er on 2011-02-07
Jaunty's repositories are still accessible (see [http://soniahamilton.wordpress.com/2009/05/02/apt-sourceslist-for-old-versions-of-ubuntu/](http://soniahamilton.wordpress.com/2009/05/02/apt-sourceslist-for-old-versions-of-ubuntu/)) but will not receive any updates.

---

### Post by kigali on 2011-02-07
Thanks, that helped, now I'm missing GL/glu.h.... 
I installed mesa-common-dev and libgl1-mesa-dev but still didn't help.

---

