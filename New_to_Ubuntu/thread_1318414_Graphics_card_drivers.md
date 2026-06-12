---
title: "Graphics card drivers"
date: 2009-11-07
forum: New to Ubuntu
---

### Post by Fhallax on 2009-11-07
I tried Ubuntu ages ago and loved it, but I kept having problems with video/sound so I switched back to Window$. Now, with a little knowledge, I've come back to the light and am trying to sort this problem out. I think it's to do with my graphics card driver. I have an ATI Radeon HD 2400 and I've tried the fglrx driver but I still have the same issue. So I've downloaded the official x86 Linux driver from the ATI site and tried to install it. Now this is where my noobosity shines through, I need root access to run the installer (it referred to it as the super-user) and I have no idea how to do this. Help, UF!

---

### Post by Fhallax on 2009-11-07
Anyone? I've figured out root access and installed the driver, but I'm still experiencing the same issue, stuttering video and weird reverberating sound.

---

### Post by Slave2Metal on 2009-11-07
This is probably a long shot...have you tried running System>Administration>Hardware drivers to see if there's a recommended driver in ubuntu?  When I first set up Jaunty, I was getting unstable graphics and the gpu fan was running high.  Checked hardware drivers, picked recommended driver by ubuntu.

---

### Post by Duskao on 2009-11-08
Hey man, what version of ubuntu are you using? You install 9.10?

Ok well, I'll give you a bit of the info for ya. 

Make sure you downloaded the newest catalyst drivers off the ati/amd website. They are the catalyst 9.10 at this point in time. 

Ok, so assuming you downloaded the file to your download folder you will want to open up a terminal and type 'cd ~/Downloads'
Then 'sudo sh ati-driver-installer-9-10-x86.x86_64.run --buildpkg Ubuntu/karmic'

If you are running a different ubuntu like 9.04 then you will substitute "Ubuntu/jaunty" for "Ubuntu/karmic", same goes for intrepid and the others.

Ok, now that you have done that you will have a few .deb files in your directory. Just go ahead and install each one of those one by one. There is one that has a dependency that isn't satasfied and you can't get it through synaptic at this point, but it's not essential so don't worry about it. But the rest should install fine. 

Once you are done installing each of the .deb files you are going to want to open up the terminal again and type in 'sudo aticonfig --initial -f'

Alright, you should be done. So now reboot and cross your fingers. Unfortunately the drivers don't seem to work for everyone which totally bites, but it works for most. 

After rebooting pull up a terminal again and type in 'fglrxinfo'
for some info about your card and driver. 

Another route you can go is to try the open source drivers, but you will have to update your kernel and then add the xorg ppa. 
You can find instructions here from the second poster
[http://ubuntuforums.org/showthread.php?t=1313828&highlight=enable+radeon+driver%3F](http://ubuntuforums.org/showthread.php?t=1313828&highlight=enable+radeon+driver%3F)

They work quite well too. Best of luck.

---

### Post by Duskao on 2009-11-08
Oh yeah, forgot to mention. If it does go badly with the official catalyst drivers then you are going to Write down or remember this series of Alt+PrntScr key combinations, just in case your screen should go black and Ctrl+Alt+F1 and Ctrl+Alt+Backspace doesn't work.
Alt+PrntScr+r, Alt+PrntScr+s, Alt+PrntScr+e, Alt+PrntScr+i, Alt+PrntScr+n, Alt+PrntScr+u, Alt+PrntScr+b
type them in slowly, a couple seconds between each one. 

Once again, best of luck.

---

### Post by lubberlick on 2009-11-08
[http://ubuntuforums.org/showthread.php?t=1315199&highlight=HD3650](http://ubuntuforums.org/showthread.php?t=1315199&highlight=HD3650) I had problems with the ATI drivers and an HD3650... my final solution can be found here... good luck.

---

