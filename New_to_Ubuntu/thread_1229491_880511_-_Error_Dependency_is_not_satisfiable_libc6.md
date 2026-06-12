---
title: "880511 - Error: Dependency is not satisfiable: libc6"
date: 2009-08-02
forum: New to Ubuntu
---

### Post by hamidi on 2009-08-02
hi
i come to use the benefits of better multitasking in a linux environment with using Avidemux in Ubuntu instead of Windows. but when i want to install the package avidemux_2.5.0-1~getdeb4_i386.deb the package installer encounters the error message i mentioned in the title.
what can i do?
thx

---

### Post by zvacet on 2009-08-02
In terminal

```
sudo apt-get install libc6
```

---

### Post by Katalog on 2009-08-02
My first question would be why wouldn't you just use Synaptic to install the version that's alreaey in the Ubuntu repositories and avoid having to deal with all the dependency headaches in the first place (unless the downloaded version has some kind of codec suport that you need or some such) ?

---

### Post by hamidi on 2009-08-02
hi zvacet!
i did it. nothing changed. in response it said that libc6 is already the newest version.
hi Katalog!
if i don't do something, it means that i don't know what to do :P
i think ur talking about System/Administration/Synaptic Package Manager.
u mean Avidemux is listed there? any third party software is listed there?
anyway, i searched for Avidemux there and nothing was found.

---

### Post by oldos2er on 2009-08-02
Make sure you have the multiverse repository enabled (System, Administration, Software Sources).

---

### Post by hamidi on 2009-08-02
an error occurred when i did it:
Could not download all repository indexes
it said that [http://archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/binary-i386/Packages.gz)
could not be found. when i checked it with Mozilla  it was confirmed.

---

### Post by oldos2er on 2009-08-02
> **hamidi said:**
> an error occurred when i did it:
Could not download all repository indexes
it said that [http://archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/binary-i386/Packages.gz)
could not be found. when i checked it with Mozilla  it was confirmed.

 Gutsy is no longer supported. You may be able to find help here: [http://old-releases.ubuntu.com/releases/gutsy/](http://old-releases.ubuntu.com/releases/gutsy/)

 I suggest you move to Ubuntu 8.04 or newer.

---

### Post by hamidi on 2009-08-02
ok
so it's better to download the latest iso and then see what problems will occur
thank u
what is the best iso url for amd64?

---

### Post by oldos2er on 2009-08-03
Go here: [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download) , and choose a download location near you.

---

### Post by hamidi on 2009-08-04
thx :)

---

### Post by hamidi on 2009-08-05
ok. i did what u said. it was installed properly without any problem. thanx :)

---

### Post by oldos2er on 2009-08-05
You're welcome. Glad you got it working!

---

