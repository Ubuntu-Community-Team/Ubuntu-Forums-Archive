---
title: "error code every time i use apt-get install"
date: 2011-05-11
forum: New to Ubuntu
---

### Post by czaravm on 2011-05-11
```
Error! Cannot locate /usr/src/bcm5974-1.1.4.dkms.tar.gz.
File does not exist.
dpkg: error processing bcm5974-dkms (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up easystroke (0.5.4-0ubuntu1) ...
Errors were encountered while processing:
 bcm5974-dkms
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

This is the error that I get every time that I try to install any package using apt-get.

Any ideas why?

---

### Post by sweetleaf on 2011-05-11
It kind of looks like you have a half-installed package. I don't know what bcm5974 is (wireless driver?), but you might try "apt-get remove bcm5974-dkms" to see if that makes apt any happier.

---

### Post by computerandu on 2011-05-11
> **czaravm said:**
> ```
Error! Cannot locate /usr/src/bcm5974-1.1.4.dkms.tar.gz.
File does not exist.
dpkg: error processing bcm5974-dkms (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up easystroke (0.5.4-0ubuntu1) ...
Errors were encountered while processing:
 bcm5974-dkms
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

This is the error that I get every time that I try to install any package using apt-get.

Any ideas why?


could you manually check whether /usr/src/bcm5974-1.1.4.dkms.tar.gz exist in the specified location..

use ls -lrt /usr/src/
or ls -lrt /usr/src/bcm5974-1.1.4.dkms.tar.gz

---

### Post by wildmanne39 on 2011-05-11
> **czaravm said:**
> ```
Error! Cannot locate /usr/src/bcm5974-1.1.4.dkms.tar.gz.
File does not exist.
dpkg: error processing bcm5974-dkms (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up easystroke (0.5.4-0ubuntu1) ...
Errors were encountered while processing:
 bcm5974-dkms
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

This is the error that I get every time that I try to install any package using apt-get.

Any ideas why?

Hi you can try these commands one at a time and then try to install again. Aslo make sure that your repositories have the main,universe,restricted and multiverse enabled in synaptic package manager. I agree that looks like a wireless card file.

sudo rm /var/lib/apt/lists/partial/*

sudo apt-get update
:)

---

