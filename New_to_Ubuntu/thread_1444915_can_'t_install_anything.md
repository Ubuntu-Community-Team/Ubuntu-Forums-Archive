---
title: "can 't install anything"
date: 2010-04-01
forum: New to Ubuntu
---

### Post by pak bear on 2010-04-01
hi there...sorry to bother u all...but i have a problem...i can't install anything using terminal...it always gave me this

faridz@ubuntu:~$ sudo apt-get install docky
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package docky

i already update it until it cannot be updated anymore...please help

---

### Post by garvinrick4 on 2010-04-01
> **pak bear said:**
> hi there...sorry to bother u all...but i have a problem...i can't install anything using terminal...it always gave me this

faridz@ubuntu:~$ sudo apt-get install docky
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package docky

i already update it until it cannot be updated anymore...please help
Just means that it cannot find a program called docky.

sudo apt-get clean
sudo apt-get install docky

I have never heard of it but make sure you have the repository open that docky resides 
in. If you do not know what repository it is in, Google it. Have a nice day.

[http://www.clububuntu.com/2009/02/how-to-install-gnome-do-docky-in-ubuntu.html](http://www.clububuntu.com/2009/02/how-to-install-gnome-do-docky-in-ubuntu.html)

There is the link, it is called gnome-do-docky.

---

### Post by 3rdalbum on 2010-04-02
Also check in System > Administration > Software Sources to see if you have the first four checkboxes (Main, Restricted, Universe and Multiverse) ticked. If these are not ticked, then your repository list will not contain Docky. When they are ticked, go into Synaptic and hit the Reload button to make sure you have the latest repository list.

---

