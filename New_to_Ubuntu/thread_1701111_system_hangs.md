---
title: "system hangs"
date: 2011-03-06
forum: New to Ubuntu
---

### Post by amitpokhrel on 2011-03-06
my system hangs whenever it tries to connect internet!! I also had this problem couple of times during the boot. Is there something I can do to prevent it??

---

### Post by Dutch70 on 2011-03-06
> **amitpokhrel said:**
> my system hangs whenever it tries to connect internet!! I also had this problem couple of times during the boot. Is there something I can do to prevent it??

Please read this...
[http://ubuntuforums.org/showthread.php?t=1422475]("http://ubuntuforums.org/showthread.php?t=1422475")

and then post the output of...
```
lspci | grep VGA
```

---

### Post by amitpokhrel on 2011-03-07
the output is:

02:00.0 VGA compatible controller: nVidia Corporation GT218 [GeForce 310M] (rev a2)

---

### Post by Dutch70 on 2011-03-07
> **amitpokhrel said:**
> the output is:

02:00.0 VGA compatible controller: nVidia Corporation GT218 [GeForce 310M] (rev a2)

Well, I've never used an nVidia graphics card. If it was Intel I may be of more help. 

Until someone with more knowledge comes along, try opening a terminal & run...

```
metacity --replace
```

See if that fixes the freezing problem for now.

---

