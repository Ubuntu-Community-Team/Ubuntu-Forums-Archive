---
title: "update manager/ synaptic manager is locked up........"
date: 2009-03-18
forum: New to Ubuntu
---

### Post by Fughley on 2009-03-18
[FONT="Book Antiqua"][/FONT]Hey everybody- I just installed the 8.10 64 bit version on my shiny new laptop and managed to gum up the synaptic package manager- BAD- here i the error message:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
I tried to do what it asked for in the terminal but no good- any ideas? 
Thanks-- the junior NooB

---

### Post by ugm6hr on 2009-03-18
```
sudo dpkg --configure -a
```

---

### Post by anaconda on 2009-03-18
I think you need to add sudo in front of that command eg.
sudo dpkg --configure -a

---

### Post by rburkartjo on 2009-03-18
yes you need to add sudo in front to work properly

---

