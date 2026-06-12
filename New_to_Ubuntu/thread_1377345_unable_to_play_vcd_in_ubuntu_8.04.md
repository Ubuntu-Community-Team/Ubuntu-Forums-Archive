---
title: "unable to play vcd in ubuntu 8.04"
date: 2010-01-10
forum: New to Ubuntu
---

### Post by idom on 2010-01-10
hi 

I am trying to play a movie VCD in ubuntu 8.04  and I am unable to play it.
mplayer gives error "seek failed" vlc does not show any error message, However, it does not play it also. 

regards,
idom.

---

### Post by wirate on 2010-01-10
May be a problem with the vcd. Try playing some other movie vcd

---

### Post by idom on 2010-01-10
I do not think that it is problem with VCD for couple of reasons 
1. the VCD plays just fine in windows. 
2. ubuntu is able to read it. as in I am able to browse through its contents without any issues in terminal as well as gui. 

Any help is appreciated. 

> **wirate said:**
> May be a problem with the vcd. Try playing some other movie vcd

---

### Post by mk1w86 on 2010-01-10
You could try:

```
sudo aptitude install ubuntu-restricted-extras
```

which will install all non-free codecs etc.

You could also try playing it in VLC.

Run:

```
sudo aptitude install vlc
```

to install VLC.

---

### Post by idom on 2010-01-12
Have already tried them both and still not helping 



> **mk1w86 said:**
> You could try:

```
sudo aptitude install ubuntu-restricted-extras
```

which will install all non-free codecs etc.

You could also try playing it in VLC.

Run:

```
sudo aptitude install vlc
```

to install VLC.

---

