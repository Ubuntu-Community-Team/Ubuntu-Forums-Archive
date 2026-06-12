---
title: "How to pipe the sound through rec to my speakers?"
date: 2009-05-24
forum: New to Ubuntu
---

### Post by Bill magee on 2009-05-24
I am using rec (a component of SoX) to digitize tapes (sound card is a Mediatek 1723 Multimedia audio controller: VIA Technologies Inc. VT1720/24 [Envy24PT/HT] PCI Multi-Channel Audio Controller). It works great.

I record a cassette side like this:

```
rec -r 48000 -c 2 myfile.wav trim 0 3000
```

But I am not getting simultaneous output from my speakers. So I want to pipe the sound to my speakers while I am recording. Can anybody tell me how to do that? 

Thanks!

Bill

---

