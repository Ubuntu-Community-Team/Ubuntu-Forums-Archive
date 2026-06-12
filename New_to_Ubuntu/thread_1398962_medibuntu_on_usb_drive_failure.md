---
title: "medibuntu on usb drive failure?"
date: 2010-02-05
forum: New to Ubuntu
---

### Post by nnjond on 2010-02-05
Hi, 
i seem to have installed the medibuntu pckges on my pen drive correctly but M player searches and stills comes back with:

No packages with the requested plugins found

The requested plugins are:

MPEG-1 Layer 3 (MP3) decoder

Your comments please.

---

### Post by Leppie on 2010-02-05
did you install the windows codecs?
```
sudo apt-get install w32codecs
```
or for x64:
```
sudo apt-get install w64codecs
```

---

### Post by nnjond on 2010-02-05
Yep.

---

