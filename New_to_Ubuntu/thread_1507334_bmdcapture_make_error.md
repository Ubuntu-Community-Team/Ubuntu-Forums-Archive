---
title: "bmdcapture make error"
date: 2010-06-11
forum: New to Ubuntu
---

### Post by buar42 on 2010-06-11
Hi, all!

I'm trying to install bmdcapture to get video from my BlackMagic Decklink card, but I'm hitting problems in the compile.

Here's what I get:
```
# make
g++ -o bmdcapture bmdcapture.cpp include/DeckLinkAPIDispatch.cpp -O3 -Wno-multichar -I include -fno-rtti -I . -lm -ldl -lpthread -lGL
/usr/bin/ld: cannot find -lGL
collect2: ld returned 1 exit status
make: *** [bmdcapture] Error 1
#

```I've searched online for "cannot find -lGL" and "ld returned 1 exit status" but all I got was info about nVidia drivers, which I don't use because I'm using an AMD videocard, CPU and (I think) chipset.

Andy

---

### Post by buar42 on 2010-06-11
I installed glutg3 and glutg3-dev and it seems to make fine now.

---

