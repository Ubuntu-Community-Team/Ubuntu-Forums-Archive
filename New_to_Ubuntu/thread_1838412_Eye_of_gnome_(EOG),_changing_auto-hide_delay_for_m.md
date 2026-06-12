---
title: "Eye of gnome (EOG), changing auto-hide delay for menu bar in fullscreen"
date: 2011-08-29
forum: New to Ubuntu
---

### Post by VinPhend on 2011-08-29
I managed it, but it needs some basic debian\ubuntu skills. Anyway this thread was the first (and only relevant) for google request "eog auto-hide toolbar".

Download source (add deb-src in your /etc/apt/source.list, apt-get source eog, apt-get build-dep eog), edit eog-window.c line

#define EOG_WINDOW_FULLSCREEN_TIMEOUT  5 * 1000

e.g.

#define EOG_WINDOW_FULLSCREEN_TIMEOUT  500

compile (cd eog-2.*.* && dpkg-buildpackage -b -uc) and install (dpkg -i eog-2.*.*.deb).

I also added to nautilus open with "eog -fc", so pressing in nautilus on picture opens it in full screen.

---

### Post by gerben1 on 2011-08-30
Thanks for your reply, I tried but could not get it working. 

I edited the source file, downloaded and installed the needed dev packages but still ended up with this:

```

pycentral: pycentral debhelper: missing XB-Python-Version attribute in package eog
pycentral: pycentral debhelper: missing XB-Python-Version attribute in package eog-dbg
pycentral: pycentral debhelper: missing XB-Python-Version attribute in package eog-dev
 dpkg-genchanges -b >../eog_2.30.0-0ubuntu1_amd64.changes
dpkg-genchanges: binary-only upload - not including any source code
dpkg-buildpackage: binary only upload (no source included)

```

---

### Post by VinPhend on 2011-09-03
> **gerben1 said:**
> Thanks for your reply, I tried but could not get it working. 

Please, execute ./configure in source folder and post here warnings, errors and summary.

---

### Post by VinPhend on 2011-09-03
e.g. I`ve got:
```
$ cd eog-2.30.2
$ ./configure > stdout.configure
$ cat stdout.configure | grep warn
checking what warning flags to pass to the C compiler... -Wall -Wmissing-prototypes
$ cat stdout.configure | grep err
checking for library containing strerror... none required
$ tail stdout.configure 
	Compiler ...................:  gcc
	Extra Compiler Warnings ....:  -Wall -Wmissing-prototypes 

	Python support .............:  yes
	EXIF support ...............:  yes
	XMP support ................:  yes
	JPEG support ...............:  yes
	Colour management support ..:  yes
	D-Bus activation............:  yes
```

---

### Post by gerben1 on 2011-09-05
When I used the commands as you suggested in your first reply there was no deb package created, but now that I looked in the src directory I saw that a working eog executable was compiled. I just copied this one over the existing eog executable in /usr/bin. It is working great now.
Thanks again

---

