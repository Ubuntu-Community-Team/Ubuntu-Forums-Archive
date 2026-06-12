---
title: "Package Install (libsdl-mixer1.2 &amp; libsdl-image1.2)"
date: 2010-11-09
forum: New to Ubuntu
---

### Post by Armeleon on 2010-11-09
I need to install the following three packages:

libsdl1.2debian-all 
libsdl-mixer1.2
libsdl-image1.2

Going to the package manger, I was able to locate and install the first (libsdl1.2.debian-all) however I could not find the second two. I assume this means I have to download the packages and somehow install them. I have no idea how to go about this. Could someone give me a couple hints on the how-to method?

**UPDATE:**

I have located and managed to install libsdl-image1.2 in the Ubuntu Software repository via the software manager. However, in trying to install libsdl-mixer1.2 I run across the error that the "Dependency is not Satisfiable: libmikmod2 (<= 3.1.10)"

---

### Post by bioterror on 2010-11-09
> **Armeleon said:**
> I need to install the following three packages:

libsdl1.2debian-all 
libsdl-mixer1.2
libsdl-image1.2

Going to the package manger, I was able to locate and install the first (libsdl1.2.debian-all) however I could not find the second two. I assume this means I have to download the packages and somehow install them. I have no idea how to go about this. Could someone give me a couple hints on the how-to method?

I got these kind of results

```
~ $ apt-cache search libsdl |grep mixer
libsdl-mixer1.2 - mixer library for Simple DirectMedia Layer 1.2


~ $ apt-cache search libsdl |grep image
libsdl-image1.2 - image loading library for Simple DirectMedia Layer 1.2
```

So if you dont find these, you might have to enable some repositories (Canonical partners?!) from your synaptics settings.

---

### Post by Armeleon on 2010-11-09
I have enabled all repositories and am still unable to find the files. However, I may be able to download them from the Internet and extract them to my computer. It is then a question of installing them. Any ideas?

---

### Post by bioterror on 2010-11-11
> **Armeleon said:**
> I have enabled all repositories and am still unable to find the files. However, I may be able to download them from the Internet and extract them to my computer. It is then a question of installing them. Any ideas?

What's your ubuntu distribution? I've got 10.04 and I have them in my repositories.

---

### Post by motonnerd on 2010-12-24
I am having a similar issue.  Here, I find that I can play videos  (though I haven't exhaustively tried every format) fine, but if I try to  convert/transcode something the screen goes blank and I get dropped back  to logon.  I even tried starting VLC in gdb, but to no avail -- it  crashed *through* the debugger.  Story of my life.

Anyway, I found similar unmet (and, according to Synaptic, unmeetable)  dependencies which are probably crashing VLC.  (but why would it bring  down the entire (I'm assuming) X server?)  Anyway, unmet dependencies  are as follows:
libsdl-image1.2-dev
        Which depends on:
        libjpeg-dev  (Which cannot be found)
        libtiff4-dev "but it is not going to be installed"
               And then going into Synaptic it tells me that this depends on  another library which     depends on libjpeg-dev, which, as I mentioned  before, does not exist.

Thoughts/workarounds?

---

