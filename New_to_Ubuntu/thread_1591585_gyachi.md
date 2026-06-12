---
title: "gyachi"
date: 2010-10-09
forum: New to Ubuntu
---

### Post by mahmoodkamal on 2010-10-09
i want to use gyachi but there is no compiled version for lucid.

can anyone tell me how to compile this is my system.

i have downloaded source from

[http://linux.softpedia.com/dyn-postdownload.php?p=9936&t=0&i=1](http://linux.softpedia.com/dyn-postdownload.php?p=9936&t=0&i=1)

---

### Post by JohnHeikkila on 2010-10-09
What is your pc's architecture?
Can you copy the output of "uname -m", please ;)

---

### Post by Jahid65 on 2010-10-09
If you use 32 bit ubuntu 10.04 then you can use the portable version of gyachi. download it from [http://portablelinuxapps.org/](http://portablelinuxapps.org/) just make it executable from properties.

---

### Post by mahmoodkamal on 2010-10-09
> **JohnHeikkila said:**
> What is your pc's architecture?
Can you copy the output of "uname -m", please ;)

i686

---

### Post by mahmoodkamal on 2010-10-09
> **Jahid65 said:**
> If you use 32 bit ubuntu 10.04 then you can use the portable version of gyachi. download it from [http://portablelinuxapps.org/](http://portablelinuxapps.org/) just make it executable from properties.

Thanks but i wanted to learn how to build in my system also.

---

### Post by andrewthomas on 2010-10-10
Do you have the build essentials

```
sudo apt-get install build-essentials automake m4 autoconf libtool
```I would read this : [https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

and use checkinstall to generate a .deb but if you want to use make install...

>     Steps for building a gyachi executable

1) use the autogen script to generate a configure script:

    ./autogen.sh

2) run configure, with any options that you might prefer:

    ./configure --disable-rpath --enable-maintainer-mode --prefix /usr

3) To generate a Fedora/RedHat spec file

    make gyachi.spec

   [B]To build an image that will be installed over existing executables
   (not recommended):[/B]

    make
    make installYou may also need some more packages

```
sudo apt-get install libjasper-dev jasper libgtkhtml3.14-dev libmcrypt-dev libv4l-dev libgpgme11-dev libgtkspell0
```I got those by looking at an arch pkgbuild
[http://aur.archlinux.org/packages/gyachi-cvs/gyachi-cvs/PKGBUILD](http://aur.archlinux.org/packages/gyachi-cvs/gyachi-cvs/PKGBUILD)

Post any errors that you get in the autogen or configure

I would read a bit more about the recommended installation

---

### Post by mahmoodkamal on 2010-10-11
i copied the source in /usr/local/src and extracted the tar file

**Output of the ./autogen.sh command**

mahmood@mahmood-laptop:/usr/local/src/Gyachi/gyachi-1.2.9$ ./autogen.sh
searching for GNU gettext intl directory...
 -> /usr/share/gettext/intl ... no
 -> /usr/local/share/gettext/intl ... no
 -> /opt/share/gettext/intl ... no
 -> /usr/gettext/intl ... no
 -> /usr/local/gettext/intl ... no
 -> /opt/gettext/intl ... no
 -> /usr/gnu/share/gettext/intl ... no
 -> /opt/local/gettext/intl ... no
 -> /opt/local/share/gettext/intl ... no
ERROR: Cannot find gettext/intl directory.
ERROR: Install GNU gettext and gettext-devel in /usr or /usr/local prefix.

Kindly guide me :confused:

---

### Post by mahmoodkamal on 2010-11-04
I got a build of gyachi for karmic from the following link:

[http://blog.sudobits.com/2010/10/24/how-to-install-gyachi-in-ubuntu-10-10/](http://blog.sudobits.com/2010/10/24/how-to-install-gyachi-in-ubuntu-10-10/)

This worked for maverick also :)

---

### Post by xeddog on 2010-11-04
Do you know of anything for 64-bit Maverick?

Wayne

---

### Post by mahmoodkamal on 2010-12-14
> **xeddog said:**
> Do you know of anything for 64-bit Maverick?

Wayne

I could not do voice chatting in gyachi, so uninstalled it. Try imo.im website.

---

