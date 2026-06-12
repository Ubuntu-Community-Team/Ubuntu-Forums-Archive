---
title: "[SOLVED] How to know whether to uncompile/remove app 1st"
date: 2008-12-12
forum: New to Ubuntu
---

### Post by Mark_in_Hollywood on 2008-12-12
Using

./configure
make
make install

I have installed ext3grep. That's a program to restore shift deleted files.

the ./configure and make worked fine, but make install returned:

make[3]: Entering directory `/opt/ext3grep-0.9.0/src'
test -z "/usr/local/bin" || /bin/mkdir -p "/usr/local/bin"
  /usr/bin/install -c 'ext3grep' '/usr/local/bin/ext3grep'
/usr/bin/install:** cannot create regular file** `/usr/local/bin/ext3grep':** Permission denied**
make[3]: *** [install-binPROGRAMS]** Error 1**
make[3]: Leaving directory `/opt/ext3grep-0.9.0/src'
make[2]: *** [install-am] **Error 2**
make[2]: Leaving directory `/opt/ext3grep-0.9.0/src'
make[1]: *** [install]** Error 2**
make[1]: Leaving directory `/opt/ext3grep-0.9.0/src'
make: *** [install-recursive] Error 1

Reading on the 'net about this take me to posts that are so far above my ability to understand the computer-ese (I'm a cookbook author, not a coder), that I dont' know what to do to help myself. 

Is there a command to uncompile the ext3grep? Or will doing the make install with a path to a directory cause the app to crash into each other? Please help, I'm lost.

---

### Post by adult swim on 2008-12-12
have you tried ```
sudo make install
```

---

### Post by Mark_in_Hollywood on 2008-12-12
I don't know whether that will work. The instructions DO NOT show a sudo or su, so I'm thinking it's NOT supposed to be root.

---

### Post by adult swim on 2008-12-12
your error was due to the fact that you didnt have permission to create the file ext3grep in the /usr/local/bin folder.  only root can write into the /usr/local/bin folder.

---

### Post by qamelian on 2008-12-12
> **Mark_in_Hollywood said:**
> I don't know whether that will work. The instructions DO NOT show a sudo or su, so I'm thinking it's NOT supposed to be root.

Since it appears to be trying to install in /usr/local/bin, you will definitely need to use ```
sudo make install
```. This will almost always be the case.

---

### Post by Mark_in_Hollywood on 2008-12-12
Someone else told me:

[COLOR="Red"]Try doing "sudo make install" so it installs into the place of your system
only root is allowed to touch.[/COLOR]

> ALSO, now that I've run make install, do I have to uninstall it before
> trying again?
[COLOR="Red"]
Because it failed, you certainly don't have to.  But anyway it should be
fine to simply overwrite a new install on top of an old install without
bothering to do 'make uninstall'[/COLOR]

---

