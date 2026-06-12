---
title: "Video Driver Problem"
date: 2010-08-29
forum: New to Ubuntu
---

### Post by itsvan on 2010-08-29
HI. im Running of ubuntu 10.04 and im having problems activating my Effects for the desktop an all of that, it says i need to activate some of my video drivers,,the problem is when i try some of the other ones, i am unable to go back to my original settings and i cant see anything anymore.for once it managed to boot back into my original settings through a command screen that i had never seen before so i restarted everything..I have an Nvidia Geforce 7800..and it gives me a list of certain drivers to pick,,,which one should i use?

Im using the nvidia accelerated graphics driver (version 173) but i cant run my effects of it

there is also version (96) and (version Current)(recommended)

---

### Post by dream_coder on 2010-08-29
Use the current version or use the nvidia ubuntu team ppa and get latest and greatest builds although more problems usually occur with newer untested builds but sometimes this is also not the case.

once you have installed new drivers open terminal and run gksudo nvidia-settings config your screen etc

Then click save as you are running as root the config settings you have made will save, in regards to compiz the latest drivers usually provide greater speeds and stability and also features etc in regards to screen effects.

Regards

---

### Post by khelben1979 on 2010-08-29
I have the same video card (nvidia Geforce7800GS) and I used version 173.14.09-5 of package nvidia-glx and the graphics worked good for everything I needed to do, including playing games with the wine application.

At the present it's not in the case because it's broken, so I cannot test any other version myself, but I would recommend the driver version, so you can test that out.

---

### Post by itsvan on 2010-08-29
Ok thank you il try it,,but now i have another problem,,ubuntu wont boot up normally,,,it goes into a black screen,,terminal like,,it asks me for my login information, i put it in,,but it stays there, apparently im logged in but in the samee terminal like screen, how can i fix this? btw this happend right after i finished doing a normal update

---

### Post by dream_coder on 2010-08-30
try typing startx after u have logged in if that fails try to reconfigure x with this command sudo dpkg-reconfigure xserver-xorg

or 

Try manually starting gnome: sudo gdm If that works do: sudo dpkg --reconfigure gdmand it will ask you to set it as a default start up.

---

