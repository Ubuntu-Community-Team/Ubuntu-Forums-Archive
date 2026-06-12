---
title: "need to completely stop x"
date: 2009-12-31
forum: New to Ubuntu
---

### Post by mamamia88 on 2009-12-31
i need to completely stop xserver from running so i can install nvidia drivers on fresh debian install.  for the life of me no matter what i do i can't get it to install.  can someone please help me?

---

### Post by SuperSonic4 on 2009-12-31
Drop to a tty by pressing **Ctrl + Alt + F1**

log in and type

```
sudo /etc/init.d/gdm stop
```

install the nvidia drivers (manually, assuming they be in ~)

```
cd
sudo ./NVIDIA-
```
 ^ use tab completion to finish the name

to restart x either reboot OR

```
sudo /etc/init.d/gdm start
```

---

### Post by mamamia88 on 2009-12-31
alt=f1 doesn't work still tells me x server is running but i found another way to install only using synaptic but thanks

---

### Post by minsf on 2009-12-31
its CTRL+alt+f1 (not just alt+f1)
actually other f's will also work: ctrl+alt+f2, ctrl+alt+f3, etc (but f7 will get you back to gnome)

---

### Post by blueridgedog on 2009-12-31
You can also kill the xserver with ctrl+ALT+Backspace.

---

### Post by SuperSonic4 on 2009-12-31
> **blueridgedog said:**
> You can also kill the xserver with ctrl+ALT+Backspace.

IIRC that is depreciated and only ever reset X

---

### Post by blueridgedog on 2009-12-31
> **SuperSonic4 said:**
> IIRC that is depreciated and only ever reset X

You are right...I just tried it.  I am getting old!

---

