---
title: "Installing files that are in tar.bz2"
date: 2010-09-08
forum: New to Ubuntu
---

### Post by Shde on 2010-09-08
How do I do this?

Thanks :)

---

### Post by bodhi.zazen on 2010-09-08
1. If at all possible use the ubunt urepositories or a ppa.

2. tar.bz2 is an archive, you have to read the README or project home page. I do not install poorly documented applications.

3. Assuming it is source code, you need to install a c compiler and the package dependencies.

```
sudo apt-get install build-essential
```Get the dependencies from the README or web site (see #2).

4. Then extract the archive, cd into the extracted directory and

```
./configure --prefix=/usr/local
make

sudo make install
```See also

[https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)

[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

---

### Post by Shde on 2010-09-08
Well, I'm trying to get Firefox 4 and Pixel. Pixel and Firefox 4 are both in tar.bz2.

Is there any way i can get these programs easier?

---

### Post by bodhi.zazen on 2010-09-08
Firefox 4 is a binary, you extract it and run it.

Detailed instructions here:

[http://support.mozilla.com/en-US/kb/Installing+Firefox+on+Linux](http://support.mozilla.com/en-US/kb/Installing+Firefox+on+Linux)

(On the firefox (mozilla) home page).

Not sure about Pixel, did you look on the Pixel home page or search the ubuntu repos or ppa ?

---

