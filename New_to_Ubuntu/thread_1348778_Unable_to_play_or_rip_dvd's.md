---
title: "Unable to play or rip dvd's"
date: 2009-12-07
forum: New to Ubuntu
---

### Post by jyanchitis on 2009-12-07
I'm using 9.10 and a Pioneer DVR-108 drive. The drive is reconized. I have tried several DVD's and I keep getting an error. I have used xine, Movie Player, dvd::rip, Thoggen, and even DVDshrink in wine. This is my first time with Ubuntu so I may be missing something simple.

---

### Post by coffeecat on 2009-12-07
What was the exact error?

Anyway, guessing what the likely problem is, first of all go to System > Administration > Synaptic and install the package ubuntu-restricted-extras which will give you a bunch of multimedia goodness that can't be shipped with Ubuntu for licensing reasons. That will also include the library livdvdread.

Next - were they commercial encrypted DVDs? You also need the library libdvdcss2 for this. Go to [medibuntu]("http://www.medibuntu.org/") and click on the 'Repository Howto' link to add the Medibuntu repository. Then install libdvdcss2. You might also want to install w32codecs or w64codecs depending on whether you are running 32-bit or 64-bit. w**codecs also comes from Medibuntu.

Next - although that should get DVD playing going OK in xine, you might want to install VLC - it's in the repos.

---

### Post by SuperSonic4 on 2009-12-07
I'm guessing you need libdvdcss2

---

### Post by jyanchitis on 2009-12-07
That was it. Thanks. Not used to being a newb again, hehe.

---

### Post by SuperSonic4 on 2009-12-07
We've all been there, don't worry about it ^.^

---

