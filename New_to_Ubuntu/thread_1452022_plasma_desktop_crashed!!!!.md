---
title: "plasma desktop crashed!!!!"
date: 2010-04-11
forum: New to Ubuntu
---

### Post by 1991sudarshan on 2010-04-11
when i rebooted my system i got a error report stating that plasma desktop was crashed!! i am getting a black screen and nothing else but i am using the run command to access the applications!! pls help!!!!:confused:

---

### Post by chemtut on 2010-04-11
Hi
Try;  Alt-F2
      Type   Konsole
             sudo apt-get install plasma-deskop
             sudo reboot

It worked for me---good luck.

---

### Post by 1991sudarshan on 2010-04-12
> **chemtut said:**
> Hi
Try;  Alt-F2
      Type   Konsole
             sudo apt-get install plasma-deskop
             sudo reboot

It worked for me---good luck.

ya i got back the plasma but i looks different!! the windows the system settings and the run command is coming on the top instead of coming in the middle!! the icons are different etc it says that the kde version is **Platform Version 4.4.2 (KDE 4.4.2)** what was the kde version given in the kubuntu 9.10?? or my kde got upgraded???

---

### Post by sandyd on 2010-04-12
> **1991sudarshan said:**
> ya i got back the plasma but i looks different!! the windows the system settings and the run command is coming on the top instead of coming in the middle!! the icons are different etc it says that the kde version is **Platform Version 4.4.2 (KDE 4.4.2)** what was the kde version given in the kubuntu 9.10?? or my kde got upgraded???

the correct version is kde 4.3. you installed kde sc backports eh? thats the only way you could have gotten 4.4

---

### Post by 1991sudarshan on 2010-04-12
> **carlee said:**
> the correct version is kde 4.3. you installed kde sc backports eh? thats the only way you could have gotten 4.4

is it possible to go the version kde 4.3???:(

---

### Post by 1991sudarshan on 2010-04-13
??????

---

### Post by sandyd on 2010-04-13
you will have to use ppa-purge to get rid of the kde sc backports ppa. search for ppa-purge in google. download it. and do ```
ppa-purge ppa:kubuntu-ppa/backports
```

---

