---
title: "nvidia graphics driver problem"
date: 2009-05-02
forum: New to Ubuntu
---

### Post by freeburn on 2009-05-02
i installed the graphics driver for nvidia card, but after installing it my screen resolution and refresh rate dropped to 800x600 and 55hz. and no options were above this,my appearance looks ugly now.but if i remove it i cant unlock the visual effects.

what should i do

---

### Post by overdrank on 2009-05-02
> **freeburn said:**
> i installed the graphics driver for nvidia card, but after installing it my screen resolution and refresh rate dropped to 800x600 and 55hz. and no options were above this,my appearance looks ugly now.but if i remove it i cant unlock the visual effects.

what should i do

Hi and what is the model of the graphics card and what version of ubuntu are you using?
Have you tried using the nvidia settings to adjust the resolution.
```
gksu nvidia-settings
```

---

### Post by freeburn on 2009-05-02
geforce 7100gs

8.04LTS


does this cmmnd provide more option than screen resolution application

---

### Post by zero7404 on 2009-05-02
do you see an icon for hardware drivers in the System pulldown ?
did you install the driver via ubuntu or did you download the package and install it manually from nvidia ?

---

### Post by freeburn on 2009-05-02
i installed it via ubuntu. what is system pulldown?(pardon my dumbness, i'm absolutely new in ubuntu)

---

### Post by overdrank on 2009-05-02
> **freeburn said:**
> geforce 7100gs

8.04LTS


does this cmmnd provide more option than screen resolution application

Yes it should. In 8.04 you will need to install it. You may use the command ```
sudo apt-get install nvidia-settings
```

---

### Post by zero7404 on 2009-05-02
you can do what overdrank suggests, or you can go to the panel -> System--> Administration, in there you will find an item called Hardware Drivers

i assume 8.04 has almost the same interface and features as 8.10...i use 8.10 and that's where i found it....

---

