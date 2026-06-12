---
title: "qtfm"
date: 2011-03-15
forum: New to Ubuntu
---

### Post by dzon65 on 2011-03-15
Does anyone know how to install qtfm? Tried nearly every available tar. Doesn't seem to contain make files.

---

### Post by LOIREE on 2011-03-15
Hey there!

In order to install qtfm, you need first to make sure you have those packages:
qt4-make qt4-dev-tools (and maybe g++ too)

Once you've installed them, just go to qtfm dir, type:
```
qmake
```It should return nothing.
Now type
```
make
```And it should start compiling!

Cheers!

---

### Post by dzon65 on 2011-03-15
Sorry for the late reply. Will give it a spin. I'll let you know.

---

### Post by dzon65 on 2011-03-15
Okay, got it. 
Regards,J.
Oh, one more question. How do I make it apply my gtk theme?

---

### Post by dzon65 on 2011-03-15
Okay, found it. Can qtfm be run in daemon-mode?

---

### Post by VastOne on 2011-07-20
> **dzon65 said:**
> Okay, got it. 
Regards,J.
Oh, one more question. How do I make it apply my gtk theme?

How did you accomplish this?

Thanks

---

### Post by VastOne on 2011-07-20
> **dzon65 said:**
> Okay, found it. Can qtfm be run in daemon-mode?
```

Command Line Parameters:

 $folder     startup folder          - qtfm will start in this folder. Starts in $HOME by default. 
 -d            daemon mode        - starts qtfm and remains running in the background.


Try adding:
 
 sleep 4s && qtfm -d &

to your '.xinitrc' file to start automatically at login.
```

---

