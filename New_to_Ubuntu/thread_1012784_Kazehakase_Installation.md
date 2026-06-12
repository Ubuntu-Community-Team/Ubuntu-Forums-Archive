---
title: "Kazehakase Installation"
date: 2008-12-16
forum: New to Ubuntu
---

### Post by Bunx on 2008-12-16
I downloaded the tar.gz file but now i'm lost as to what to do with it. Help would be very much appreciated.

---

### Post by nandemonai on 2008-12-16
> **Bunx said:**
> I downloaded the tar.gz file but now i'm lost as to what to do with it. Help would be very much appreciated.

Don't worry about trying to install it from source. It's already on the universe repo.

Simply make sure you have the universe repo enabled then:

```
sudo apt-get update && sudo apt-get install kazehakase
```

;)

---

### Post by Bunx on 2008-12-16
Yeah but I heard the repository version is severely out of date...any truth to this?

---

### Post by nandemonai on 2008-12-16
> **Bunx said:**
> Yeah but I heard the repository version in severely out of date...any truth to this?

Package: kazehakase
Priority: optional
Section: universe/web
Installed-Size: 1960
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Original-Maintainer: Hidetaka Iwai <tyuyu@debian.or.jp>
Architecture: amd64
Version: 0.5.4-2.1ubuntu3
Provides: www-browser
Depends: libatk1.0-0 (>= 1.20.0), libc6 (>= 2.4), libcairo2 (>= 1.2.4), libfontconfig1 (>= 2.4.0), libfreetype6 (>= 2.3.5), libgcrypt11 (>= 1.4.0), libglib2.0-0 (>= 2.16.0), libgnutls26 (>= 2.4.0-0), libgtk2.0-0 (>= 2.14.1), libice6 (>= 1:1.0.0), libpango1.0-0 (>= 1.21.6), libpixman-1-0, libpng12-0 (>= 1.2.13-4), libsm6, libtasn1-3 (>= 0.3.4), libx11-6, libxcb-render-util0, libxcb-render0, libxcb1, libxrender1, zlib1g (>= 1:1.1.4), kazehakase-gecko | kazehakase-webkit, ruby1.8, libgtk2-ruby, libgettext-ruby1.8
Recommends: hyperestraier
Suggests: migemo
Conflicts: kazehakase-migemo
Filename: pool/universe/k/kazehakase/kazehakase_0.5.4-2.1ubuntu3_amd64.deb
Size: 708100
MD5sum: 84e695f69ae75d4ebba1e2fbb4fa21e7
SHA1: 20f794b6ca494b3e43a31bb29abda25d9a3b04e1
SHA256: 36a7ed32a9b8c4b2cbf73b92f0800857ea9687d10074ef7deb9c4b1b5c379611
Description: GTK+-base web browser that allows pluggable rendering engines
 Kazehakase is a web browser that can use either Gecko or WebKit as
 its rendering engine.
 .
 Kazehakase has a toolbar with rss/rdf menus, rss/rdf viewer, normal bookmarks,
 search window for google.  These are to be available as plugins.
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu

That's the latest if I'm not mistaken.

---

### Post by Bunx on 2008-12-16
Indeed it is! Thank you for that! :D

---

### Post by nandemonai on 2008-12-16
> **Bunx said:**
> Indeed it is! Thank you for that! :D

No worries mate. Enjoy :)

---

### Post by Bunx on 2008-12-16
Okay new problem. I installed Kazehakase and I love how quick and simple it is but it has no Java support...or does it? Anyone want to enlighten me? Or tell me of some other lightweight browsers that have Java support?

---

