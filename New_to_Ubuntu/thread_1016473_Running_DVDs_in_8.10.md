---
title: "Running DVDs in 8.10"
date: 2008-12-19
forum: New to Ubuntu
---

### Post by ArcticWalrus on 2008-12-19
Failure to mount error. How to correct?

---

### Post by taurus on 2008-12-19
What kind of DVD is it?  Which release are you running?

---

### Post by ArcticWalrus on 2008-12-19
Dolby Digital from a CD

---

### Post by ArcticWalrus on 2008-12-19
8.10 Ubuntu

---

### Post by ArcticWalrus on 2008-12-19
Why do I need permissions to run a DVD how do I get them.............

---

### Post by taurus on 2008-12-19
Do you belong to group cdrom?

```
id
```

---

### Post by ArcticWalrus on 2008-12-19
> **taurus said:**
> Do you belong to group cdrom?

```
id
```

gid=1000(----------) groups=4(adm),20(dialout),24(cdrom),46(plugdev),108(lpadmin),123(admin),124(sambashare),1000(------)

---

### Post by ArcticWalrus on 2008-12-20
I'm honestly going to but windows again tomorrow if I can't get this solved... as much as I would not like to... help

---

### Post by bumanie on 2008-12-20
Have you installed multi-media codecs from medibuntu? You need them to be able to play most cd/dvd discs. Go [here]("https://help.ubuntu.com/community/Medibuntu") and follow the instructions. I would suggest installing vlc player after that, it plays nearly every codec. > sudo apt-get install vlc

---

### Post by hyper_ch on 2008-12-20
> **ArcticWalrus said:**
> I'm honestly going to but windows again tomorrow if I can't get this solved... as much as I would not like to... help

Bye bye...

---

