---
title: "[SOLVED] Terminal for installation of Soundcard drivers"
date: 2009-01-05
forum: New to Ubuntu
---

### Post by loseby on 2009-01-05
Trying to install the drivers for my Soundblaster X-fi soundcard. Have downloaded the drivers but need some help with the instructions.

In terminal,


1) Goto source directory
 ??????
2) Execute make command as root
????????
   make

   make install
?????????

---

### Post by zvacet on 2009-01-06
If your driver comes in tar.gz then you have to decompress it by right click on it and select **unpack here** (or something similar;I don´t use English version).If you downloaded it in your home directory just open terminal and then 

```
cd name_of_your_driver_folder
```

after that

sudo make
sudo make install

if you posted right commands

If you downloaded driver on desktop then type in terminal

```
cd Desktop
```

and following commans are same

---

### Post by loseby on 2009-01-09
Thankyou for that 

I think something work because now in sound preferences the xi-fi alsa is there.

---

