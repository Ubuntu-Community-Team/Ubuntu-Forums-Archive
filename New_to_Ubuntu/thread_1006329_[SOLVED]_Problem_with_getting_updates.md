---
title: "[SOLVED] Problem with getting updates"
date: 2008-12-09
forum: New to Ubuntu
---

### Post by Yudraciell on 2008-12-09
As the title says i need to get some updates but i cant get the required packages for some of the updates...i really dont want to do it half***ed either (linux aint microsoft lol) I want to be thourough about it... the packages i cant get are from original domain

```
W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/i/initramfs-tools/initramfs-tools_0.85eubuntu39.2_all.deb
  404 Not Found [IP: 91.189.88.46 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/a/app-install-data-commercial/app-install-data-commercial_9.3_all.deb
  404 Not Found [IP: 91.189.88.46 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/h/hal-info/hal-info_20081001-0ubuntu1~hardy1_all.deb
  404 Not Found [IP: 91.189.88.46 80]


```

i assume these are important files...or work together with one or more of the other updated packages, any tips on what i can do

---

### Post by Yudraciell on 2008-12-09
to solve my own question i forgot to update my package manager

for those who dont know

open up terminal
```

sudo apt-get update
```

---

