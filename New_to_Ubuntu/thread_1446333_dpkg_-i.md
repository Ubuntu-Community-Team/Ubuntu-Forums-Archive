---
title: "dpkg -i"
date: 2010-04-03
forum: New to Ubuntu
---

### Post by 3948ctyj on 2010-04-03
I have been on UBU for over 1.5 years and I have NEVER been able to install a package in the terminal..
I have downloaded FF 3.6 to the Desktop and yes I cd to that...I actually right clik and I have an option to open terminal in that directory.  
Anyway sudo dpkg -i  doesnt work...
sudo dpkg -i package   doesnt work....
sudo  make-install doesnt work..
what  does work?????????????????????

---

### Post by RealPSL on 2010-04-03
What is the name of the file you downloaded. dpkg -i would work with a .pkg file. If you are trying to install outside without a package e.g. .tar.bz2 file there are instructions here [http://support.mozilla.com/en-US/kb/Installing+Firefox+on+Linux?bl=n&s=installing%20firefox%20on%20linux&as=q]("http://support.mozilla.com/en-US/kb/Installing+Firefox+on+Linux?bl=n&s=installing%20firefox%20on%20linux&as=q")

---

### Post by yetiman64 on 2010-04-04
@RealPSL

> What is the name of the file you downloaded. dpkg -i would work with a [COLOR=Blue].pkg[/COLOR] file. Ah, isn't that a .deb or are there .pkg files that work as well:confused:

---

### Post by 3rdalbum on 2010-04-04
> **3948ctyj said:**
> I have been on UBU for over 1.5 years and I have NEVER been able to install a package in the terminal..
I have downloaded FF 3.6 to the Desktop and yes I cd to that...I actually right clik and I have an option to open terminal in that directory.  
Anyway sudo dpkg -i  doesnt work...
sudo dpkg -i package   doesnt work....
sudo  make-install doesnt work..
what  does work?????????????????????

What do the instructions say?

sudo dpkg only works on Debian packages.

make and sudo make install only work on source code.

Firefox is usually a straight binary file that you run:

```
./firefox
```

(assuming that the directory you are in contains a file called 'firefox').

---

