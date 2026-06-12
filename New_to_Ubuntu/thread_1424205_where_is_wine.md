---
title: "where is wine??"
date: 2010-03-07
forum: New to Ubuntu
---

### Post by 3948ctyj on 2010-03-07
Wine doesnt seem to be in synaptic..??where??

---

### Post by steveneddy on 2010-03-07
What version of Ubuntu are you using?

Did you try

```
sudo apt-get install wine
```

???

---

### Post by SecretFace on 2010-03-07
or use PlayOnLinux...it installs Wine too.
website: [http://www.playonlinux.com/en/](http://www.playonlinux.com/en/)

---

### Post by candtalan on 2010-03-07
in the Universe repository I think. 
Try using 
Applications>Add/Remove
and if there is a choice, set to 
'all available' not just 'supported'

That should be ok, but a more advanced approach would be to ensure that in
System>Administration>Software Sources
you have
community maintained (Universe) checked

then look for wine

hth

---

### Post by ajgreeny on 2010-03-07
Or if you want to try the most up-to-date version go to [http://www.winehq.org/download/deb](http://www.winehq.org/download/deb) and follow the instructions to add the repository.

---

