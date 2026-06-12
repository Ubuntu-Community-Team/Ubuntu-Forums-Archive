---
title: "Finding Drivers"
date: 2011-02-08
forum: New to Ubuntu
---

### Post by Mr.TAMER on 2011-02-08
Hello :)
 
I have just began to use ubuntu with a group of my friends, and I'm responsible for finding video card drivers.
 
Do you have any idea about how to quickly find drivers (generally or Video), especially for laptops?
any links? (this will be very useful)
any problem solving links?
 
thanks in advance :)

---

### Post by Frogs Hair on 2011-02-08
System > Administration > Additional Drivers or Hardware and Drivers for the desktop version . This installs proprietary drivers. I don't use the netbook version and you haven't said what versions your friends are using. Welcome to the forums.

---

### Post by Mr.TAMER on 2011-02-08
> **Frogs Hair said:**
> System > Administration > Additional Drivers or Hardware and Drivers for the desktop version . This installs proprietary drivers.
 
Thanks :)
 
We're using ubuntu 10.10 (and some use 10.4, since we are about 30 members!). 
 
But I may not have an internet connection, so how do I get the backages? ( links maybe :oops: )
 
And how do I know whether a driver has been successfully installed or not?
 
if not... how do I solve the problem?
 
sorry for asking alot, but I'm still a beginner.

---

### Post by Frogs Hair on 2011-02-08
When the driver jockey is opened it will automatically search for drivers , often there will be more than one choice and I use the recomennded one . The driver/s will download and install and there will be a restart notice . Proprietary drvers may affect the appearance of the splash screen , so don't be supprised .
 
I use a wired internet connection and never had problems. Sorry I can't offer any help with wireless drivers. The documentation and methods for using wireless on Ubuntu may vary depending on what wireless system is used.

---

### Post by 3rdalbum on 2011-02-08
"How do I know if the drivers are installed?"

If you get 3D acceleration (you can run Google Earth, the desktop effects, or any other 3D program) then you have 3D drivers.

Basic video drivers are preinstalled with the Ubuntu system. If you have Intel graphics, then the official drivers are preinstalled and there's nothing else you need to do. If you have ATI Radeon graphics (not Radeon HD) then you already have the only drivers for your card.

If you have ATI Radeon HD or Nvidia graphics, you really should get an internet connection to install them. Frankly, with Ubuntu you need an internet connection - it's too much hassle without one. You could, possibly, get the "nvidia-current" or "fglrx" packages from [http://packages.ubuntu.com](http://packages.ubuntu.com) and install them, but then you have to manually download all the dependencies and subdependencies too. Too much work. Get an internet connection on the Ubuntu machines.

---

### Post by Mr.TAMER on 2011-02-08
Thanks for answers :)
 
but does this work for both normal ubuntu and wubi? or there are other accounts for wubi?
 
actually it's very beneficial to ask here, so may I ask you about audio cards and wireless cards too?
 
thanks.

---

### Post by Paqman on 2011-02-08
Wubi works just the same as normal Ubuntu for this.

Audio cards should just work, but wifi often needs proprietary drivers, which you can get through the Additional Drivers tool. You might need to plug straight into your router with an ethernet cable so you can get online to download the wifi drivers.

---

