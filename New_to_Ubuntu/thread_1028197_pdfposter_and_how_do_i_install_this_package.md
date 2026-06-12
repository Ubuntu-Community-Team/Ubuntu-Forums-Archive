---
title: "pdfposter and how do i install this package"
date: 2009-01-02
forum: New to Ubuntu
---

### Post by minkynink on 2009-01-02
Hi all .And Happy New Year .
Ive just migrated from XP 2 days ago to ubuntu and im having a few head scratching problems .
Ive downloaded a pdfposter package from [http://pdfposter.origo.ethz.ch/download/650](http://pdfposter.origo.ethz.ch/download/650)  to my desktop and am now stumped as to how i install it .
I use tiled printing for my clothes design and pattern making so do need it .
Can anyone guide me in the right direction please ?

Many thanks in advance 

Mink

---

### Post by HotShotDJ on 2009-01-02
> **minkynink said:**
> Can anyone guide me in the right direction please ?I just clicked on the installation instructions from the pdfposter web page and found this: [http://svn.origo.ethz.ch/wsvn/pdfposter/trunk/README.txt](http://svn.origo.ethz.ch/wsvn/pdfposter/trunk/README.txt)

You need to install the requirements first... Python should already be installed (double check your system via Synaptic Package Manager for python2.5) and python-pypdf is also installable via Synaptic.

I assume you've already downloaded the tar.gz file that you linked us to.  Right-click on it and choose "Extract Here" from the pop-up menu.  Now you should be able to follow the instructions in the link I gave you.

(It looks like a cool program!  Good luck with it!)

---

### Post by minkynink on 2009-01-02
Hi . 
Thanks for the reply , will go and see if im successful this time . 

Mink

---

### Post by minkynink on 2009-01-02
Im still confused as to how i install the pdfposter .
If anyone could help me in a step by step hand holding install session i will be eternally grateful . 
Thanks

Mink

---

### Post by asynchronous13 on 2009-08-05
I know it's probably too late to help the original poster, but just in case someone else finds this thread, the following command worked for me:

```
sudo easy_install pdfposter
```

---

