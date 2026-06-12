---
title: "install VLC media player"
date: 2010-04-24
forum: New to Ubuntu
---

### Post by computerguts on 2010-04-24
I recently installed Linux 10.04 and it has been running great since I had so much trouble with karmic 9.10

I have a windows computer that has an internet connection but on my Linux computer I do not have an internet connection and the router that is connected to the windows computer is a great distance from my Linux computer. So there is really no way to install packages on Linux without a great deal of hassle. Is there any way that I can install packages by downloading them on the windows computer and installing them on the Ubuntu Linux computer. 

Thanks

---

### Post by The Thunder Chimp on 2010-04-24
> **computerguts said:**
> I recently installed Linux 10.04 and it has been running great since I had so much trouble with karmic 9.10

I have a windows computer that has an internet connection but on my Linux computer I do not have an internet connection and the router that is connected to the windows computer is a great distance from my Linux computer. So there is really no way to install packages on Linux without a great deal of hassle. Is there any way that I can install packages by downloading them on the windows computer and installing them on the Ubuntu Linux computer. 

Thanks


Yes there is, follow this link to download package files individually from any machine. Place them on removable media, and place the file on your Ubuntu computer.

[http://packages.ubuntu.com/lucid/](http://packages.ubuntu.com/lucid/)

Tell me if it worked!

---

### Post by computerguts on 2010-04-24
no.............. it did't work

thanks anyway though

---

### Post by computerguts on 2010-04-24
correction, it would work fine if you could satisfy all the dependencies.

---

### Post by 3rdalbum on 2010-04-24
> **computerguts said:**
> no.............. it did't work

thanks anyway though

How exactly didn't it work? You also need to dowbload each dependency - for instance, VLC depends on 'vlc-data' and 'libqt' and others. All the dependencies are linked from the package's page on that site.

When you have all the necessary packages, you double-click them on the Ubuntu machine, dependencies first and VLC itself last, to install.

In this scenario a lot of people suggest AptOnCd, but I have never tried this method. Google will tell you more.

---

### Post by achase79 on 2010-04-24
AptOnCd is great if you have another connected linux machine, but if you only have a windows or mac available then i would suggest [keryx]("http://www.keryxproject.org")

---

### Post by dearingj on 2010-04-24
> **3rdalbum said:**
> 
When you have all the necessary packages, you double-click them on the Ubuntu machine, dependencies first and VLC itself last, to install.


Another option, if you have a lot of dependencies and want to avoid lots of double-clicking, is to open a terminal, cd to the folder where the .deb files are, and enter:
```
sudo dpkg -i *.deb
```

This will install all the .deb files at the same time.

---

### Post by taqkavar on 2010-04-24
I recommend using [uspc]("http://code.google.com/p/uspc/") , however you may have to wait until the patch for Lucid is out.

---

### Post by computerguts on 2010-04-24
keryx would work great if when you went to the windows directory a black terminal window in windows comes up. 

How could I fix this?

---

### Post by computerguts on 2010-04-24
it does work but you have to download all the dependencies seperatly and install them in order. 

Thanks a bunch

---

### Post by The Thunder Chimp on 2010-04-25
You could always go for aptoncd by installing Ubuntu in Windows on your PC (as a program I mean). That should work.

---

### Post by computerguts on 2010-04-25
what do you mean?

the suggestion you made earlier works great but is very time consuming.

---

