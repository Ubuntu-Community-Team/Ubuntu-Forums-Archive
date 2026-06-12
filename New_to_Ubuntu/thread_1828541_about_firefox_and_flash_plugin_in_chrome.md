---
title: "about firefox and flash plugin in chrome"
date: 2011-08-19
forum: New to Ubuntu
---

### Post by gr8ansh4u on 2011-08-19
i recently installed ubuntu
ubuntu is detecting the network but firefox is not able to connect to network so that i can browse...

**_1st question: y firefox is not able to connect to internet_**

now i installed chrome...
its working but flash plugin is not installed..i downloaded .tar.gz archive from net..._**2nd quesion...how to install .tar.gz archive?**_

thanks in advance :..:)

---

### Post by mikewhatever on 2011-08-19
> **gr8ansh4u said:**
> i recently installed ubuntu
ubuntu is detecting the network but firefox is not able to connect to network so that i can browse...

**_1st question: y firefox is not able to connect to internet_**

Detecting the network is good, but not good enough to be able to browse the internet. You have to be connected.

> 
now i installed chrome...
its working but flash plugin is not installed..i downloaded .tar.gz archive from net..._**2nd quesion...how to install .tar.gz archive?**_

thanks in advance :..:)

I suggest installing flash from the Software Center. Search for 'Adobe' and install the 'Adobe Flash Plugin' package.
To answer the question, tar.gz is not an installation file, it's an archive. You can't install it, pretty much all there is to do is unpack it or extract the content. In this particular case, one of the included files would be 'libflashplayer.so'. If you copy that file to a proper location (/usr/lib/mozilla/plugins), flash will work.

---

### Post by gr8ansh4u on 2011-08-19
> Detecting the network is good, but not good enough to be able to browse the internet. You have to be connected.


ubuntu is showing that i'm connected but still firefox is not able to connected...but chrome does...y so? do i have to configure something in firefox?

---

### Post by gr8ansh4u on 2011-08-19
and wen i try to move 'libflashplayer.so' file to (/usr/lib/mozilla/plugins)...error occurs saying that permission is denied...

---

### Post by mikewhatever on 2011-08-19
Make sure File->Work Offline is not checked in Firefox.

Sure, that's outside your home folder. I really only posted that as information and not something meant to follow. The Software Center has an uptodate version of Adobe Flash, no reason not to use it.

---

