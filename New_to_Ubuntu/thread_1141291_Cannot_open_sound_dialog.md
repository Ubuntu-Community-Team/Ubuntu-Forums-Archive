---
title: "Cannot open sound dialog"
date: 2009-04-28
forum: New to Ubuntu
---

### Post by pzs on 2009-04-28
I've just upgraded to Jaunty and I've lost sound in mpg321, flash, Amarok... I have to use OSS because I have an obscure sound card. osstest shows sound is working. I suspect I need to just set everything to oss, but the System->Preferences->Sound dialog does not launch. Any ideas?

---

### Post by pzs on 2009-05-04
In fact, each individual app needed its own debug. I had to reinstall flash for 64 bit Linux using this page:

[http://www.cyberciti.biz/tips/install-flash-10-ubuntu-linux-64bit.html](http://www.cyberciti.biz/tips/install-flash-10-ubuntu-linux-64bit.html)

You have to explicitly tell mpg321 to use oss using the -o flag.

To fix Amarok, I installed systemsettings from the package manager and moved oss to the top of the audio priorities. 

I still can't open my sound dialog.

---

