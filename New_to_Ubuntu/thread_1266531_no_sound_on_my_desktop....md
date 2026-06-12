---
title: "no sound on my desktop..."
date: 2009-09-14
forum: New to Ubuntu
---

### Post by I WILL DO IT on 2009-09-14
i dont think my intel drivers is installed, can some one hellp?

---

### Post by k33bz on 2009-09-14
by any chance have you tried using alsamixer?

If not go into the terminal
```
alsamixer
```

You can adjust values there, sometimes these are muted or turned all the way down.

---

### Post by I WILL DO IT on 2009-09-14
cool@cool-desktop:~$ alsamixer

alsamixer: function snd_ctl_open failed for default: No such file or directory
cool@cool-desktop:~$ sudo alsamixer

alsamixer: function snd_ctl_open failed for default: No such file or directory
cool@cool-desktop:~$

---

### Post by k33bz on 2009-09-14
```
sudo apt-get install alsa
```

after installation then run
```
alsamixer
```

---

### Post by I WILL DO IT on 2009-09-14
cool@cool-desktop:~$ sudo apt-get install alsa
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting alsa-base instead of alsa
alsa-base is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
cool@cool-desktop:~$ alsamixer

alsamixer: function snd_ctl_open failed for default: No such file or directory
cool@cool-desktop:~$

---

### Post by k33bz on 2009-09-14
mmmm, then lets try it with the GUI option

```
sudo apt-get install alsamixergui
```

you should then be able to run it, it will be either in sound and video or system settings under application

---

### Post by I WILL DO IT on 2009-09-14
cool@cool-desktop:~$ sudo apt-get install alsamixergui
[sudo] password for cool: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
alsamixergui is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
cool@cool-desktop:~$

---

