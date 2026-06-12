---
title: "How to activate Nvidia drivers terminal style?"
date: 2009-03-10
forum: New to Ubuntu
---

### Post by Ben Page on 2009-03-10
Yes, How to activate Nvidia drivers terminal style? I have somehow deleted the deamon (or whatever it is called) that activates the proprietary drivers, so how to activate them CLI way, or what package is the GUI?

Note that I have installed the drivers, just need to activate them...

---

### Post by skymera on 2009-03-10
Install envy from the repos then 

```
 sudo apt-get install envyng-core 
``` (Might be wrong slighty, it's either envy-core or envyng-core)

Then run with

```
 sudo envy -t 
```

---

### Post by sp176 on 2009-03-10
I am not sure how to answer your question.  I had install my drivers by using system/administration/restricted drivers manager

---

### Post by xXNI4NI on 2009-03-10
would a re-install be out of order?

---

### Post by Ben Page on 2009-03-20
No reinstall neded, the app that I needed was gnome or gdm-jockey, for KDE its KDE-jockey, thats that app called "restricted hardware drivers". So in synaptyc its easy to download...This happened to me when I installed my package cache to a fresh installation, drivers and ewverithing installed correctly, but the "jockey" was gone (?)...
Anyway, I know this thread is dead, but just incase anybody will stumble upon this problem, there it is a simple sollution.

---

