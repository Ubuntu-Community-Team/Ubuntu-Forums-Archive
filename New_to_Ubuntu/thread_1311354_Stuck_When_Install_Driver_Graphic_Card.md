---
title: "Stuck When Install Driver Graphic Card"
date: 2009-11-02
forum: New to Ubuntu
---

### Post by Arphitz on 2009-11-02
Please...
help me out...
Now Im using HP Laptop DV4 - 1137tx
Then i install Ubuntu 9.10(64 bit) on my lappy.
all driver are installed except my graphic card.
after that i check at NVIDIA website for the newest driver. so i found out the latest driver is  NVIDIA-Linux-x86_64-190.42-pkg2.run .
for your information i already put the files almost all the main folders
eg : (home,downloads,desktop,music,....etc..etc...)

the problem is...i already followed all the method that showed at forum and others website...the result still the same(failed)...

So i cannot fully utilized my lappy. I very appreciate if someone can help me to settled this problem.

Really need help you guys...

thanks...cheers...

---

### Post by aktiwers on 2009-11-02
This is how you** should **install the driver:
[http://www.psychocats.net/ubuntu/nvidia](http://www.psychocats.net/ubuntu/nvidia)



If thats not working for you, and you want to try the manuel install, this is how:

Make sure the file is in your home folder.

Open terminal and type:
```
sudo aptitude install libc6 libc6-dev
``````
sudo aptitude install build-essential linux-headers-$(uname -r);
``````
sudo chmod +x NVIDIA-Linux-x86_64-190.42-pkg2.run
```Close all your apps and save all your documents and go to fullscreen terminal(CTRL+ALT+F1) and login.

Stop gdm from running(gdm most be stopped to use the installer):
```
sudo /etc/init.d/gdm stop
```then run the installer:
```
sudo ./NVIDIA-Linux-x86_64-190.42-pkg2.run
```when done reboot:
```
sudo reboot
```and you should be done :)

---

### Post by Arphitz on 2009-11-02
Yeah!!!

Thanks to aktiwers !!!! ;)

I have to go for manual method...
appreciate much !!!

Now my lappy in the right track!!!


:)

---

### Post by aktiwers on 2009-11-03
Glad it worked - now I forgot to tell you that everytime you get a kernel update
you will probably have to reinstall the drivers :(

Lucky that kernel updates are not that often, but when it happens you must reinstall (or install the newest driver you can find).

Cheers glad to help.

---

### Post by Toke on 2009-11-05
> **aktiwers said:**
> Glad it worked - now I forgot to tell you that everytime you get a kernel update
you will probably have to reinstall the drivers :(

Lucky that kernel updates are not that often, but when it happens you must reinstall (or install the newest driver you can find).

Cheers glad to help.

Thanks, this was useful.
:D

(the steps above, that is)

---

