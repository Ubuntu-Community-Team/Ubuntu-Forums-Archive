---
title: "nvidia 180.29 drivers SLI help"
date: 2009-03-09
forum: New to Ubuntu
---

### Post by championboxes on 2009-03-09
Has anybody got the 180.29 Nvidia drivers to work on an SLI system?  Ive tried to install them several times but cant get them to work... In another thread for installing the 177 drivers i had to add a line in the xorg file under the section "Device" I had to add BusId "07:00:00" I have tried this with the new drivers but still cant get them to work...

---

### Post by skymera on 2009-03-09
How are you installing the drivers?

---

### Post by championboxes on 2009-03-09
I would download the drivers from the nvidia site then i would do sudo sh ./NVIDIA... which i could never get that to work...

but I found something interesting in another thread ```
 sudo apt-get install nvidia-180-kernel-source nvidia-180-modaliases nvidia-glx-180

``` which that installed the 180.11 drivers not the 180.29 is there something similar that i could apt-get install the newest drivers?

---

