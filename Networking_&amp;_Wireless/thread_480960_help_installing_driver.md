---
title: "help installing driver"
date: 2007-06-22
forum: Networking &amp; Wireless
---

### Post by bensor on 2007-06-22
I have presario 2100 and trying to follow this link:
[http://bnmr.triumf.ca/~zaher/Presario_2197CA/#Wireless:](http://bnmr.triumf.ca/~zaher/Presario_2197CA/#Wireless:)
Ifirst I could  get ndiswrapper recognized even though I had it in the directory (failed at make install)

So I tried (not sure if it was the right thing):
[I]2.2.1. Feisty Fawn (7.04) and Edgy Eft (6.10)
For 7.04 Feisty Fawn 
[http://packages.ubuntu.com/feisty/mi...wrapper-common](http://packages.ubuntu.com/feisty/mi...wrapper-common) 
[http://packages.ubuntu.com/feisty/mi...pper-utils-1.9](http://packages.ubuntu.com/feisty/mi...pper-utils-1.9) 
[http://packages.ubuntu.com/feisty/net/ndisgtk](http://packages.ubuntu.com/feisty/net/ndisgtk) [/I]

[I]Copy the appropriate files over to a directory on your Ubuntu computer (e.g. your Home directory) and install them in this order: 

sudo dpkg -i ndiswrapper-common_*.deb

sudo dpkg -i ndiswrapper-utils*.deb

sudo dpkg -i --force-depends ndisgtk_*.deb[/I]


now ndiswrapper is installed and no recognizing error is sent.

But now when I try
ndiswrapper -i bcmwl5.inf
I get
couldn't create /ect/ndiswrapper/bcmwl5:Permission denied at /usr/sbin/ndiswrapper-1.9 line 146

What am I doing wrong?

---

### Post by kevdog on 2007-06-22
Please so the other post where you first posted this question.  I answered it there.

---

