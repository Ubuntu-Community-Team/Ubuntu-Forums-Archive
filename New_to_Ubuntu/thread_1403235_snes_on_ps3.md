---
title: "snes on ps3"
date: 2010-02-10
forum: New to Ubuntu
---

### Post by rwh824 on 2010-02-10
Ok I am brand new to Ubuntu and have been struggling all day to get it to work. My main purpose is to be able to play snes on my ps3. I keep getting the error cannot find package snes9express. How do I fix this?

---

### Post by Satoru-san on 2010-02-10
```
apt-cache search snes
```

Nintendo on a play station >_<

Its possible that package you wanted its renamed to something else. so that command will search the repositories for "snes" you can also try "nintendo" <- without quotes.

Good luck

---

### Post by nhasian on 2010-02-10
Running ubuntu on a PS3 is gonna be god awful slow with only 256 megs of ram available to the system plus its not an x86 processor so you will need to compile most software youself unless you can find it packaged for that type of processor so you will not have a pleasant experience with either linux or ubuntu. :(

i bought a PS3 myself when they first launched with the intention of using it as an HTPC and I was sorely disappointed.  It was so slow it wouldnt even play high definition files in linux.  sure it can play bluray through sony's dashboard but not in linux!  

at the time i was using yellowdog linux and the snes9x that was prepacked was broken so i had to compile it myself to get it to run.  I never did get the ps3 controller to work wirelessly though...

overall if you could get a used computer off of craigs list for $100 you will be much much happier.

---

### Post by 3rdalbum on 2010-02-10
I have responded to your other thread - snes9express is in Universe, and you can add the Universe repository by a simple click of a checkbox in System > Administration > Software Sources. Then you can install this program.

---

