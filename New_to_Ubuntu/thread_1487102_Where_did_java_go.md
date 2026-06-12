---
title: "Where did java go?"
date: 2010-05-18
forum: New to Ubuntu
---

### Post by SpinningAround on 2010-05-18
I'm trying to install sun-java6-plugin, but apt-get say there is no such package, in fact i can't find a single sun java package. Could someone please give me advice in how to get around this problem?

---

### Post by QIII on 2010-05-18
Enable the Universe and Multiverse repos.

Search for java-6-sun in Synaptic.


Edit:  Crap!  I just saw your version.  What is below is for Lucid.

It is in the "partner" repository now.

See my posts here:

[http://wwww.ubuntuforums.org/showthread.php?p=9219854](http://wwww.ubuntuforums.org/showthread.php?p=9219854)

To make Sun Java your default (if you have OpenJDK still installed):

```
sudo update-java-alternatives -s java-6-sun
```

---

### Post by SpinningAround on 2010-05-18
Thanks :)

---

### Post by QIII on 2010-05-18
Just happened to think (I hope you come back) that the older repos have Update 15, which has some security issues.

To add the latest Update 20, look here:

[http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)

---

