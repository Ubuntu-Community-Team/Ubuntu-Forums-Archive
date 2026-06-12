---
title: "help me with visual effects!!"
date: 2009-09-03
forum: New to Ubuntu
---

### Post by yanibha on 2009-09-03
hiiii,
      i am a new ubuntu user starting just yesterday nite... many of the necessary updates, updates, codecs etc , i have successfully installed... thanks to the threads displayed in these ubuntu forums... i have just one problem... i want to activate extra visual effects in my laptop but im getting a error like this

SystemError: Failed to lock /var/cache/apt/archives/lock

i have the normal nvidia graphics card in my hp laptop....

sos... pl help me ... what should i do...

---

### Post by jbrown96 on 2009-09-04
This is usually caused by having update manager, synaptic, hardware drivers, or some other software installation program open. It could also be caused by one of those programs closing unexpectedly and not removing the lock. 

the easiest solution is to restart. if that doesn't work, run ```
sudo rm /var/cache/apt/archives/lock
``` then it should work properly.

---

