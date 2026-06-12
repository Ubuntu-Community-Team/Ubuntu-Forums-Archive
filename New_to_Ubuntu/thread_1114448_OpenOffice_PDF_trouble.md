---
title: "OpenOffice PDF trouble"
date: 2009-04-02
forum: New to Ubuntu
---

### Post by drumfire420 on 2009-04-02
I'm having an issue with exporting a paper for my physics class.   It all looks great, in open office.  When exported to a PDF (so that my teacher will accept it) several of the numbers within equations turn to gook (see attached screen shot, yes red arrows were added later).  I've tried setting the PDF Options to lossless images, but that did not help much.

Any help greatly appreciated.

---

### Post by _Purple_ on 2009-04-02
Looks like the numbers are displayed in arabic after the file is converted into pdf format. It is a bug. You can check [here](https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/244353).

---

### Post by albinootje on 2009-04-02
> **_Purple_ said:**
> Looks like the numbers are displayed in arabic after the file is converted into pdf format. It is a bug. You can check [here](https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/244353).

This link talks about a solution, says that it is solved in 2.4.1 in june 2008.
[http://user.services.openoffice.org/en/forum/viewtopic.php?f=7&t=4233](http://user.services.openoffice.org/en/forum/viewtopic.php?f=7&t=4233)
That makes me think OOO 3.x would be good for you.
Here's a howto for installing 3.x on Ubuntu Hardy (Also works on Intrepid)
[http://www.howtoforge.com/how-to-install-openoffice-3.0.0-on-ubuntu-8.04](http://www.howtoforge.com/how-to-install-openoffice-3.0.0-on-ubuntu-8.04)

---

### Post by drumfire420 on 2009-04-02
Thanks, that was the issue.  It appears that bug is still not fixed, however using the cups-pdf printer is a good workaround.

My physics grade is very appreciative.

---

### Post by Lunx on 2009-04-02
Bit late for me to offer help as I see there's been a solution found, but I will still mention it as you may want to think about giving it a try later. There's an application in the repositories called Scribus which I find excellent for creating PDFs. Scribus is a desktop publishing app, rather than a word processor and it's really good for all sorts of document layouts.

---

