---
title: "Desktop Effects could not be anabled."
date: 2009-05-19
forum: New to Ubuntu
---

### Post by rvgsd on 2009-05-19
Hi all,  

I have ATI Radeon Mobility 7500 graphics card, and the open source drivers installed which came default with Ubuntu 8.04.
I am not able to enable the desktop effects after installing compiz.

If I run the command **compiz** in the terminal:
```

laptop@laptop9:~$ compiz
Checking for Xgl: not present. 
Found laptop using ati driver. 
aborting and using fallback: /usr/bin/metacity 

```

Help please.

Dell inspiron 5100
2.4 Ghz single core processor, 
1 Gig RAM 
ATI Radeon 7500 Graphics card.
Ubuntu 8.04.

---

### Post by rvgsd on 2009-05-19
My problem is solved, I installed **xgl-xserver** and compiz worked !

---

