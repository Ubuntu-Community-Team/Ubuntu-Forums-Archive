---
title: "How to uninstall Ubuntu 10.10"
date: 2010-10-14
forum: New to Ubuntu
---

### Post by hduguay on 2010-10-14
I installed ubuntu 10.10 and I want downgrade back my previous version. Is there a way to do this without reformatting my machine ?

Any help on this issue would be greatly appreciated.

---

### Post by HermanAB on 2010-10-14
Nope, but if you created a separate /home partition, then don't format that and al your data and desktop settings will be retained.

---

### Post by ibizatunes on 2010-10-14
out of luck kid o! put / and /home on separate partition as rebuild your box

---

### Post by lexdave on 2010-10-14
Best method is going to be to copy your /home folder to an external drive, and then copy it back once you've reformatted with the previous version.

Also, I remember there being a method that you could download a copy of your installed programs, so that you could just have Ubuntu go out and re-download those after you reinstall the OS.  Does anybody else remember how to do that, it may have been a third party app even.

---

### Post by Nightstrike2009 on 2010-10-14
Hiya Lexdave,

> 
Also, I remember there being a method that you could download a copy of your installed programs, so that you could just have Ubuntu go out and re-download those after you reinstall the OS. Does anybody else remember how to do that, it may have been a third party app even.

Do you mean *aptoncd* from the repos?

To Install enter terminal and type:

sudo apt-get install aptoncd

Bobs your uncle then just find it on your ubuntu bar, and select *create* or *restore* as appropriate, it restores your apt cache but you still have to issue install commands but saves you from redownloading them :-)

---

### Post by Quackers on 2010-10-14
There's this method
[http://www.arsgeek.com/2006/09/19/ubuntu-tricks-how-to-generate-a-list-of-installed-packages-and-use-it-to-reinstall-packages/](http://www.arsgeek.com/2006/09/19/ubuntu-tricks-how-to-generate-a-list-of-installed-packages-and-use-it-to-reinstall-packages/)

---

