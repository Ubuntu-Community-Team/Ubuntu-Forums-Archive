---
title: "what does this error code mean"
date: 2010-01-08
forum: New to Ubuntu
---

### Post by Fika on 2010-01-08
I tried to install rootkit hunter ( sudo apt-get install chkrootkit ) to see how it works and I got this:

Errors were encountered while processing:
 ttf-mscorefonts-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)

I've got this error before

32 bit karmic koala 9.10

Thanks

---

### Post by juancarlospaco on 2010-01-08
sudo apt-get purge ttf-mscorefonts-installer ; sudo apt-get clean

---

