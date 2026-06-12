---
title: "Where am I messing up in my Java installation?"
date: 2010-01-10
forum: New to Ubuntu
---

### Post by SixthDeclension on 2010-01-10
I followed these directions here:

[http://www.java.com/en/download/help/5000010500.xml#enable](http://www.java.com/en/download/help/5000010500.xml#enable)

and got here:

> nick@nick-can-count-to-42:/usr/lib/mozilla-firefox/plugins$ ln -s /home/nick/jre1.6.0_17/plugin/i386/ns7/libjavaplugin_oji.so
ln: creating symbolic link `./libjavaplugin_oji.so': File existsAfter that, nothing is happening, Java isn't showing up as a plugin. Where did I mess up?

---

### Post by tom.swartz07 on 2010-01-10
> **SixthDeclension said:**
> I followed these directions here:

[http://www.java.com/en/download/help/5000010500.xml#enable](http://www.java.com/en/download/help/5000010500.xml#enable)

and got here:

After that, nothing is happening, Java isn't showing up as a plugin. Where did I mess up?

That guide doesnt seem too Ubuntu savvy. It might be outdated.

Heres a better guide:
I would suggest removing everything related to Java and using this. 

[http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java) 
Theres a guide for 32 and 64 bit OS's, 32bit is the left column, 64 is the right.

Good luck!

---

### Post by SixthDeclension on 2010-01-10
Thank you very much. That guide mentioned Heron, which was the disk I had laying around when I installed, and I just used synaptic.

---

