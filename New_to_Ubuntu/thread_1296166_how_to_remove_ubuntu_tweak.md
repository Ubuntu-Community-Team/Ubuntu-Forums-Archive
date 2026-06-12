---
title: "how to remove ubuntu tweak?"
date: 2009-10-20
forum: New to Ubuntu
---

### Post by SheroEg on 2009-10-20
al salam alaykum..
 
i installed ubuntu tweak and i regretted it after it hurdled updates and caused synaptic to close automatically..
 
i tried to remove it with all apt-get commands, and i failed..
 
i tried to remove its data from status file in the dpkg, and the file is read only..
 
how to fix this problem?

---

### Post by philinux on 2009-10-20
```
sudo apt-get remove --purge ubuntu-tweak
```

Or in synaptic highlight ubuntu tweak right click and select completely remove.

---

### Post by nos09 on 2009-10-20
or you can use add or remove programme to remove it. just uncheck it and then apply the changes.
but it is recommanded that you use synaptic or terminal to remove it.

in terminal: 
code:

sudo apt-get remove --purge ubuntu-tweak

---

### Post by wilee-nilee on 2009-10-20
> **SheroEg said:**
> al salam alaykum..
 
i installed ubuntu tweak and i regretted it after it hurdled updates and caused synaptic to close automatically..
 
i tried to remove it with all apt-get commands, and i failed..
 
i tried to remove its data from status file in the dpkg, and the file is read only..
 
how to fix this problem?

 If it caused synaptic to close it is because your not supposed to run both at the same time; like a apt terminal function and synaptic. I suspect that you may not understand it's function, and used it incorrectly. What the heck is hurdled updates.

---

### Post by yellowpike on 2011-11-09
Had the same situation and did the following
Installed to ubuntu 11.10 Synaptic Manager using

```
sudo apt-get install synaptic
```

Opened Synaptic Manager and did a complete removal of 
ubuntu-tweak-0 (version 0.5.15-0~20111023~oneiric1)Ubuntu Configuration Tool

Installed ubuntu-tweak (version 0.6.0-0~20111108+bzr1612~oneiric1)

using code found @

[http://www.noobslab.com/2011/09/install-ubuntu-tweak-on-ubuntu-1110.html]("http://www.noobslab.com/2011/09/install-ubuntu-tweak-on-ubuntu-1110.html")

Worked well for me!
Regards
yellowpike

---

### Post by Frogs Hair on 2011-11-09
The version 5.14 will cause dependency problems . Do as suggested above if you want to Use Ubuntu Tweak .

---

### Post by Mark Phelps on 2011-11-09
Unless they've changed it recently, v6 of Ubuntu Tweak is a BETA and missing some functionality from v5.

---

