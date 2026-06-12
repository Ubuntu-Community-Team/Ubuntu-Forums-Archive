---
title: "help install Nvidia graphic"
date: 2010-03-29
forum: New to Ubuntu
---

### Post by panjeran on 2010-03-29
i have a vaio vpccw16fg and i newbie also... 
please help me if i want to installing my Nvidia 
i using karmic koala 9.10 amd64
step by step please... regards

---

### Post by Linuxforall on 2010-03-29
> **panjeran said:**
> i have a vaio vpccw16fg and i newbie also... 
please help me if i want to installing my Nvidia 
i using karmic koala 9.10 amd64
step by step please... regards

system>administration>hardware drivers 

See if any drivers are listed, enable them and reboot, thats all.

---

### Post by Laxman_prodigy on 2010-03-29
> **panjeran said:**
> i have a vaio vpccw16fg and i newbie also... 
please help me if i want to installing my Nvidia 
i using karmic koala 9.10 amd64
step by step please... regards


Go to "System" and to "Administration" and to "Hardware drivers"; a window shall open, click on the recommended one and "Activate".:P

You should have active internet connection to do so.

---

### Post by panjeran on 2010-03-29
thanks for the advice....
i like that words.. both of you
makes me more excited:D

---

### Post by panjeran on 2010-03-29
my screen is going black
please .. what should i do

---

### Post by boxcorner on 2010-03-29
> **panjeran said:**
> my screen is going black
please .. what should i do
Your computer or screen might be in a power saving mode.  Try moving your mouse around, or pressing a key on the keyboard.

System > Administration > NVIDIA X Server Settings
to see the NVIDIA Driver Version

---

### Post by panjeran on 2010-03-29
its not working

---

### Post by panjeran on 2010-03-29
> **boxcorner said:**
> Your computer or screen might be in a power saving mode.  Try moving your mouse around, or pressing a key on the keyboard.

System > Administration > NVIDIA X Server Settings
to see the NVIDIA Driver Version

i cannot login to windows... its just dark blank,,thanks

---

### Post by realzippy on 2010-03-29
press Alt+Ctrl+F2,login,type:

```
startx
```

what happens?

---

### Post by readycarpenter on 2010-03-29
> **panjeran said:**
> i cannot login to windows... its just dark blank,,thanks

are you running ubuntu or windows? or dual boot and it will not work in windows either? if that is the case it could be a hardware issue..

---

### Post by panjeran on 2010-03-29
> **readycarpenter said:**
> are you running ubuntu or windows? or dual boot and it will not work in windows either? if that is the case it could be a hardware issue..

im using dualboot, ubuntu and win7.. 
in win7 no problem, its just fine..

---

### Post by lidex on 2010-03-29
Boot into recovery mode - should be second option in grub menu. Let that do it's thing and when it asks you what you want to do, choose the command prompt option (not sure of exact wording), login and enter this command:
```
sudo mv /etc/X11/xorg.conf xorg.conf.old
```

Reboot

---

