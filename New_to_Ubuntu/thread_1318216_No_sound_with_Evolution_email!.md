---
title: "No sound with Evolution email!"
date: 2009-11-07
forum: New to Ubuntu
---

### Post by daje10 on 2009-11-07
Hello everybody,
I'm new to Ubuntu, I'm coming from XP and Leopard too, sick of windows I decided to try Linux Ubuntu as alternative. I'm runnning the last version, the 9.10, everything works pretty good and I really like my new os, a lot. 
Two things though don't seems to work at all: email notification sound on evolution and also iTunes. 
I know that iTunes doesn't run on Linux, I made my homework and I've found out that it could run through Wine. So, now I've Wine and iTunes v7.3 but again, no sound from songs on iTunes. 
For sumarize, I've no sounds on my email notification (Evolution) and no sounds from songs on iTunes 7.3.
Hope to get some help, I'm pretty desperate at this point!! 
Thanks to all

---

### Post by lisati on 2009-11-09
> **daje10 said:**
> 
Two things though don't seems to work at all: email notification sound on evolution and also iTunes. 


I wish to confirm that the sound doesn't seem to work with Evolution on 9.04 as well..... I honestly hadn't noticed!

---

### Post by mbzn on 2009-11-09
I've read somewhere in the forum (cant find it now) that under Add/remove there is 'mail-notification' and '(not sure about this one) evolution-notification'. If i remember correctly, install the one that is not installed and it should be fine.

---

### Post by philinux on 2009-11-09
This has been reported at launchpad.

A workaround is possible using a script. I've called mine playsoundforemail.sh but that choice is yours The content is only a two liner. You need to put your sound file somewhere too. 

Then just make a new filter e.g email sender contains @. Then run program and point to the script.

```
#! /bin/bash
aplay ~/.evolution/dialog-question.wav
```

To get it to work every email turn off evolutions notification plugin.

[https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/292585](https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/292585)
See post #15

---

