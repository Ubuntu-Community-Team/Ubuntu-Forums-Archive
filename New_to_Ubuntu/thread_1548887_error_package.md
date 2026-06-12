---
title: "error package"
date: 2010-08-09
forum: New to Ubuntu
---

### Post by godjer on 2010-08-09
I have a problem :( : 
subprocess installed post-removal script returned error exit status 1
Errors  were encountered while processi...ng:
 audacious-skins
E: Sub-process  /usr/bin/dpkg returned an error code (1)

Can somebody help me? please

---

### Post by zeroseven0183 on 2010-08-09
Try running this command in the Terminal
```
sudo aptitude update
sudo aptitude -f install
```

---

