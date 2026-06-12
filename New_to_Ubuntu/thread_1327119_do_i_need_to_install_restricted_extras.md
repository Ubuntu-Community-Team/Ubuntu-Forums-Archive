---
title: "do i need to install restricted extras?"
date: 2009-11-15
forum: New to Ubuntu
---

### Post by kapi on 2009-11-15
Morning all,

when using 8.10 I had to add restricted extras (from what I remember) to access codecs for dvd etc.

I had a look in the software source in system>preferences> administration.
 it seems it's already installed. 

what do I do now? I feel like an idiot, i had a really good grasp of linux and now I feel like I'm back at the start of the learning curve.

---

### Post by 3rdalbum on 2009-11-15
Restricted Extras installs everything except DVD decryption (libdvdcss2) and w32/64codecs; those can be installed by adding the Medibuntu repository ([www.medibuntu.org](www.medibuntu.org)) and installing the libdvdcss2 and non-free-codecs packages.

---

### Post by camaron1 on 2009-11-15
> **kapi said:**
> Morning all,

when using 8.10 I had to add restricted extras (from what I remember) to access codecs for dvd etc.

I had a look in the software source in system>preferences> administration.
 it seems it's already installed. 

what do I do now? I feel like an idiot, i had a really good grasp of linux and now I feel like I'm back at the start of the learning curve.
If you upgraded then they are installed, that's it

---

### Post by coffeecat on 2009-11-15
The package ubuntu-restricted-extras is not included by default in a fresh installation of Ubuntu. If it's there...

* You must have installed it, or...

* You've done an upgrade from a previous version and u-r-e was upgraded along with the rest, or...

* You are running Linux Mint.

Which is it? :wink:

By the way, +1 to what 3rdalbum said. the lack of libdvdcss2 and w**codecs in ubuntu-restricted-extras baffles a lot of people.

---

### Post by donato roque on 2009-11-15
If you want to find out if a particular package is installed or not just go to the gnome-terminal.  Press alt+f2.  Type aptitude.  Try search. Start typing the package name.  A letter "i" before the package means it's installed.

---

### Post by bacardiandwatermelon on 2009-11-15
I thought you didn't need to use the medibuntu repo anymore as the libdvdread4 package is avaliable?

---

### Post by coffeecat on 2009-11-15
> **bacardiandwatermelon said:**
> I thought you didn't need to use the medibuntu repo anymore as the libdvdread4 package is avaliable?

Libdvdread4 is provided by ubuntu-restricted-extras, but have another look at 3rdalbum's post. You need libdvdcss2 for encrypted DVDs, hence you need Medibuntu if you want to play encrypted DVDs. 

From package descriptions:

libdvdread4:

> libdvdread provides the functionality that is required to access many DVDs. It
parses IFO files, reads NAV-blocks, and performs CSS authentication and
descrambling.

libdvdread currently uses libdl to dynamically probe for libdvdcss at runtime.
If found, libdvdcss will be used to decrypt sections of the DVD as necessary.

Canonical does not provide updates for libdvdread4. Some updates may be provided by the Ubuntu community.libdvdcss2:

> To allow applications to access some of the more advanced features
of the DVD format.

---

