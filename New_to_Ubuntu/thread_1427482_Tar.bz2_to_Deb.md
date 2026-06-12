---
title: "Tar.bz2 to Deb"
date: 2010-03-11
forum: New to Ubuntu
---

### Post by LunaticHiatus on 2010-03-11
This is just something generally handy to know and I have no idea how to do it.

---

### Post by marshmallow1304 on 2010-03-11
tar.bz2 is just a compressed archive.  Assuming it's source code, the general procedure would be to extract the archive, enter the new directory in the terminal, then

```
./configure
make
sudo checkinstall -D --install=no
```
(If you want to also install the deb, leave off "--install=no".  The "-D" is not necessary on a Debian-based system, but it won't hurt anything.)

checkinstall will run through a prompt.  The answers don't really matter all that much unless you plan to distribute the deb.


For this to work, you'll need build-essential and checkinstall installed if they aren't already.
```
sudo apt-get install build-essential checkinstall
```


Edit: If you wanted to use a more official method, see [this guide]("https://wiki.ubuntu.com/PackagingGuide").

---

