---
title: "Cant Install vlc..."
date: 2009-05-12
forum: New to Ubuntu
---

### Post by kamitsukai on 2009-05-12
I'm trying to install the VLC nightly repository on ubuntu 8.10 amd64 but after adding it to sources.list and then running

```
sudo apt-get update
```

I get the error

```
W: Failed to fetch http://nightlies.videolan.org/build/intrepid-amd64/arch/./Packages.gz  404 Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.

```

---

### Post by Keithhed on 2009-05-12
Maybe you will have better luck using the package manager?

---

### Post by kamitsukai on 2009-05-12
> **Keithhed said:**
> Maybe you will have better luck using the package manager?

afraid not...

---

### Post by binbash on 2009-05-12
Did you try this repo ? :

[http://www.ubuntu-inside.me/2009/04/howto-fix-integrated-video-bug-at-vlc.html](http://www.ubuntu-inside.me/2009/04/howto-fix-integrated-video-bug-at-vlc.html)

---

### Post by kamitsukai on 2009-05-12
> **binbash said:**
> Did you try this repo ? :

[http://www.ubuntu-inside.me/2009/04/howto-fix-integrated-video-bug-at-vlc.html](http://www.ubuntu-inside.me/2009/04/howto-fix-integrated-video-bug-at-vlc.html)


Is that nightly builds...?

---

### Post by kamitsukai on 2009-05-13
bump...

---

### Post by mc4man on 2009-05-13
Unless something has changed recently there are no 'nightly builds' available and haven't been for some time (broken server

you can get a daily source here, and build yourself or as suggested add a ppa that has a recent 1.0 build

[http://nightlies.videolan.org/build/source/?C=M;O=D](http://nightlies.videolan.org/build/source/?C=M;O=D)

---

