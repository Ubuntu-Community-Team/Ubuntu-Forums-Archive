---
title: "Installing something when the power went out."
date: 2010-05-31
forum: New to Ubuntu
---

### Post by genis200 on 2010-05-31
I was installing a TV application when the power went out. N[HTML][/HTML]ow, I'm unable to install anything, and I get the error ```
installArchives() failed
``` and ```
Errors were encountered while processing:
 mythtv-database
 mythtv-frontend
E: Sub-process /usr/bin/dpkg returned an error code (1)

```as well as ```
dpkg (subprocess): unable to execute installed post-removal script: Exec format error
dpkg: error processing mythtv-database (--remove):
 subprocess installed post-removal script returned error exit status 2
Removing mythtv-frontend ...
dpkg (subprocess): unable to execute installed post-removal script: Exec format error
dpkg: error processing mythtv-frontend (--remove):
 subprocess installed post-removal script returned error exit status 2
Errors were encountered while processing:
 mythtv-database
 mythtv-frontend
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by yeats on 2010-05-31
try:

```
sudo apt-get -f install
```

which should fix the broken packages

---

