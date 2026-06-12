---
title: "Unsupported sound card"
date: 2009-07-05
forum: New to Ubuntu
---

### Post by donjur on 2009-07-05
I just installed ubuntu 9.04 (my first foray into Linux) and cannot get any sound.  I tried several solutions suggsted on the forum until I read EbuggingSound Problems and was directed to 
[https://help.ubuntu.com/community/SoundTroubleshooting?action=show&redirect=DebuggingSoundProblems](https://help.ubuntu.com/community/SoundTroubleshooting?action=show&redirect=DebuggingSoundProblems)
.My sound card was recognized but not supported.  I have Intel ICH8 and according to the site that lists supported sound cards, the latest Intel card was ICH8.  Any idea how to get my sound card supported?

---

### Post by cariboo on 2009-07-06
the ICH8 sound chipset should be supported, could you open an Applications-->Accessories-->Terminal and type a few commands to help in trouble shooting, first type:

```
lspci | grep Audio
```

and

```
lsmod | grep snd
```

The first command list what the model of your sound card, and the second command lists the drivers that are loaded for your sound card. Paste the output of both commands in your next post.

---

