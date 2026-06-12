---
title: "IDLE for python in UBUNTU"
date: 2011-02-02
forum: New to Ubuntu
---

### Post by nadsun on 2011-02-02
I need to install a IDLE for python 2.6.6 under UBUNTU. 
After trying 'sudo apt-get install idle-python2.6 ', 
shell returns:
'E: Unable to locate package idle-python2.6
E: Couldn't find any package by regex 'idle-python2.6'

Please, anyone out there to help?  Any idea where to get this package from and how to make it run?
Thank you.

---

### Post by cipherboy_loc on 2011-02-02
```

sudo apt-get install idle

```should install it. Next time, try opening up Synaptic (**gksudo synaptic**) and typing in: **idle python** in the Quick Search bar.



Cipherboy

---

### Post by nadsun on 2011-02-02
Thanks for your suggestion, checked in synaptic manager, no package. 
Can you, please, recommend any good site for downloading it?

Thanks.

---

### Post by cipherboy_loc on 2011-02-02
Ah, you need to enable the universe and multiverse repositories. See [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)    for more help.


Cipherboy

---

### Post by nadsun on 2011-02-02
Thank you, Cipherboy! 
That's it!

---

### Post by Steve H on 2011-12-18
> **cipherboy_loc said:**
> ```

sudo apt-get install idle

```should install it. Next time, try opening up Synaptic (**gksudo synaptic**) and typing in: **idle python** in the Quick Search bar.



Cipherboy


Thanks, that helped me as well.

---

