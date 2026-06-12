---
title: "nvidia xconfig missing"
date: 2009-09-19
forum: New to Ubuntu
---

### Post by Dominik AOK on 2009-09-19
first of all, i've looked at lots of forums before i posted this, so i have (a tiny) idea of what might be wrong.

but...
upon startup the ascii reads: [fail] upon trying to install nvidia driver automatically.
i can't bot the computer unless i do it in recovery mode.

i went to hardware drivers where it suggested the nvidia 173... so i clicked "activate", it downloaded, but it continued to stay grey and say unactivated.

the card is a gforce 5200 128bit.

i tried to run 
sudo nvidia-xconfig, as root, and it didnt do anything either.

does nayone know why it might not let me install this driver?

---

### Post by Bachstelze on 2009-09-19
From a terminal, try

```
sudo apt-get install build-essential linux-generic linux-headers-`uname -r`
sudo apt-get install nvidia-glx-173
```

---

