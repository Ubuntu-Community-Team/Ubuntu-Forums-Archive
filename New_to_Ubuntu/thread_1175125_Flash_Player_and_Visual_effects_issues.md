---
title: "Flash Player and Visual effects issues"
date: 2009-05-31
forum: New to Ubuntu
---

### Post by x8illy8oyx on 2009-05-31
Hey I like to say hi to everyone on my first post, I just installed ubuntu 9.04 on my new WD 1 TB external HDD to try it on and see whats the fuzz about, i really really like it but I have 3 issues with it, first i cant enable the extra visual effects not even the normal ones, I did a research about it but I couldnt found anything to help me out being a real noob in linux, I also have problems installing adobe flash player because when I download the one from the webpage it says wrong architecture i386 and im downloading the one with extention .deb wich i think is the correct one
 
If anyone can help me out ill really appreciate it!

---

### Post by aagavin on 2009-05-31
> i cant enable the extra visual effects not even the normal ones

First have you tried enabling the your Graphics Card Drivers by:

```
System -> Administration -> Hardware Drivers
```
and then select the graphics and the wireless.


>  I also have problems installing adobe flash player because when I download the one from the webpage it says wrong architecture i386 and im downloading the one with extention .deb wich i think is the correct one

To get flash open up your terminal **Applications -> Accessories -> Terminal ** and type in: 

```
sudo apt-get install flashplugin-nonfree
```

---

### Post by Six-Blade Knife on 2009-05-31
about the visual effects you probably have to install third-part drivers: go system->hardware driver (or third party drivers, depending on your language) and see if you are using the graphic card drivers (most likely you are not). activate them if not already. this will make you download/install the needed packages and after that you will have to restart the system (or at least session).
given that you  have a relatively new box..
about the flash player you can install via Synaptic flashplugin-nonfree,restarting your browser

---

### Post by x8illy8oyx on 2009-06-01
The thing for the flash player did work thank you :D, and i did try to activate the proprietary drivers but whenever i go to **System-Administration-Hardware drivers** it tells me that no proprietary drivers are in use on this system, and it doesnt give the option to do anything...

---

