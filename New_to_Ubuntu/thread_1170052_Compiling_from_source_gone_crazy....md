---
title: "Compiling from source gone crazy..."
date: 2009-05-25
forum: New to Ubuntu
---

### Post by melrokz on 2009-05-25
what is this? what should I do to get this compiled (simple explanations are appreciated)

> checking for 	 glib-2.0 >= 2.4.0                	 libgnome-2.0 >= 2.7.0	 libnautilus-extension >= 2.8.0... Package libgnome-2.0 was not found in the pkg-config search path. Perhaps you should add the directory containing `libgnome-2.0.pc' to the PKG_CONFIG_PATH environment variable No package 'libgnome-2.0' found Package libnautilus-extension was not found in the pkg-config search path. Perhaps you should add the directory containing `libnautilus-extension.pc' to the PKG_CONFIG_PATH environment variable No package 'libnautilus-extension' found
configure: error: Library requirements (	 glib-2.0 >= 2.4.0                	 libgnome-2.0 >= 2.7.0		 libnautilus-extension >= 2.8.0) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.

I do have libnautilus-extension 2.26 and glib 2.18 (I compiled it).
Now what to do?

---

### Post by elliotn on 2009-05-25
If it say some files are not found: that means u must satisfy dependencies first, those files need to be installed first b4 u can compile

---

### Post by melrokz on 2009-05-25
I know, but Why does it show this when I have the latest versions installed?
> 
I do have libnautilus-extension 2.26 and glib 2.18 (I compiled it).

---

### Post by Crafty Kisses on 2009-05-25
First make sure you have this package installed:
```
sudo apt-get install build-essential
```
Then usually when you want to compile a file from source, you have to run the following commands:
```
./configure
make
make install
```
Then if it has unsatisfied dependencies it should let you know, then you need to grab the ones it tells you.

---

### Post by oldos2er on 2009-05-25
When compiling you need the -dev versions of dependencies, e.g. libnautilus-extension-dev

---

### Post by Tibuda on 2009-05-25
> **melrokz said:**
> I know, but Why does it show this when I have the latest versions installed?

Do you have the *-dev packages installed? Maybe libnautilus-extension-dev

---

### Post by melrokz on 2009-05-25
libnautilus-extension-dev is not to b seen in the repos ???

---

### Post by melrokz on 2009-05-25
source code software source is enabled...

---

### Post by oldos2er on 2009-05-25
Hmm. It's in the Jaunty repos. Not sure why it wouldn't be available for 8.10 too.

---

### Post by melrokz on 2009-05-25
in 'software sources', the 'source code' section is only shaded, not ticked. I can't tick it either. Is this why I dont get it in the repos? How may I correct this problem?

---

### Post by BoyOfDestiny on 2009-05-26
No, that's not the problem. The source code, well as with gpl software, you distribute the binary, you need to offer the source too. 
That's what the source repository is, for you to build the software offered in the repositories (i.e. the same version Ubuntu offers.)

What software are you trying to build?
Try this command, replace APP with the name of the software 
```
sudo apt-get build-dep APP
```
If there is a version in the Ubuntu repos, it will gather the build dependencies... Perhaps the version you want has same/similar dependencies...

---

