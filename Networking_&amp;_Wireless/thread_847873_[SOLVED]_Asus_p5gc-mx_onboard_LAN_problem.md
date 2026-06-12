---
title: "[SOLVED] Asus p5gc-mx onboard LAN problem"
date: 2008-07-03
forum: Networking &amp; Wireless
---

### Post by rijalul on 2008-07-03
Dear all,

I've just install hardyheron on my friend PC. That PC use Asus p5gc-mx motherboard and onboard LAN card. I have a problem with onboard LAN, ubuntu doesn't recognized that. How can I fix that? I have download *.tar.gz from asus website that support driver for linux. How to use that driver? How to install that?

Sorry, I'm newbie in ubuntu and linux

Many thanks before.

---

### Post by nixscripter on 2008-07-03
That package contains a kernel module.

Here are the general steps, done in Terminal:

1. Unpack the tarball (the kind of file you downloaded): ```
tar zxf **file**.tar.gz
``` with **file** in place of the file name.

2. Make sure you have the linux source for the install: ```
sudo apt-get install linux-headers-generic
``` Some packages will download; say "yes" to all questions.

3. Change into the directory and build the driver:
```
 cd **file**
./configure
make
sudo make install

```

4. Try loading the module with the **modprobe** command. The card should be recognized.

Hope this helps.

---

### Post by rijalul on 2008-07-07
Thanks for your help...
My friends PC run smoothly now...

:)

---

### Post by nixscripter on 2008-07-08
I'm glad. Please mark this thread as SOLVED (under the Thread Tools menu).

---

