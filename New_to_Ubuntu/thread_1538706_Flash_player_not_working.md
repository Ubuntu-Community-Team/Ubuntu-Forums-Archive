---
title: "Flash player not working"
date: 2010-07-25
forum: New to Ubuntu
---

### Post by Junaid Ali on 2010-07-25
I am using ubuntu 10.04 and my flash player is not working properly, 

For example while playing You tube video I can not play-pause by clicking on the video 

or I can not cancel add at the bottom of the video etc 

Can any one suggest a solution please

---

### Post by Jazzy_Jeff on 2010-07-25
Are you using 32 or 64 bit Ubuntu?

---

### Post by lovinglinux on 2010-07-25
This usually happens when you are using the 32bit plugin on a 64bit system. If this is the case, then you need to edit the npviewer file. 

Open it with the command below:

```
gksudo gedit /usr/lib/nspluginwrapper/i386/linux/npviewer
```

Then add the following line before the last line of that file:

```
export GDK_NATIVE_WINDOWS=1
```

The file content should look like this:

```
#!/bin/sh
TARGET_OS=linux
TARGET_ARCH=i386
export GDK_NATIVE_WINDOWS=1
. /usr/lib/nspluginwrapper/noarch/npviewer
```

Save the file and restart the browser.

---

### Post by Junaid Ali on 2010-07-27
> **lovinglinux said:**
> This usually happens when you are using the 32bit plugin on a 64bit system. If this is the case, then you need to edit the npviewer file. 

Open it with the command below:

```
gksudo gedit /usr/lib/nspluginwrapper/i386/linux/npviewer
```Then add the following line before the last line of that file:

```
export GDK_NATIVE_WINDOWS=1
```The file content should look like this:

```
#!/bin/sh
TARGET_OS=linux
TARGET_ARCH=i386
export GDK_NATIVE_WINDOWS=1
. /usr/lib/nspluginwrapper/noarch/npviewer
```Save the file and restart the browser.


Thanx its working now

---

### Post by ultrageeky on 2010-07-27
Thanks LovingLinux, I wondered how to fix it.

---

