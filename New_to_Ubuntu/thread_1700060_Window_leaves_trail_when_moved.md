---
title: "Window leaves trail when moved"
date: 2011-03-04
forum: New to Ubuntu
---

### Post by anotherdummhead on 2011-03-04
I've installed pretty much everything that needed to be installed, i'm using X1300 and i've typed in terminal :

> sudo /usr/share/ati/fglrx-uninstall.sh  # (if it exists)
sudo apt-get remove --purge fglrx*
sudo apt-get remove --purge xserver-xorg-video-ati xserver-xorg-video-radeon 
sudo apt-get install xserver-xorg-video-ati
sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
sudo dpkg-reconfigure xserver-xorg
sudo apt-get install fglrx-modaliases

Then installed d3dx9, vcredist2008 and everything else from winetricks, and still windows leave trails when they're moved. What's the problem here?

---

### Post by Hippytaff on 2011-03-04
What graphics card do you have? and are you using the full compiz sherbang!?

---

### Post by anotherdummhead on 2011-03-04
Radeon X1300...and i'm new in whole Ubuntu stuff, i didn't understand what you've posted up there :D

---

### Post by Hippytaff on 2011-03-04
Actually I'm not sure about xubuntu, whether it uses compiz...compiz is just fancy desktop efforts, but it takes a lot to use it to it's full potential. I wouldn't imagine xfce (which is the desktop for xubuntu as opposed to Gnome for ubuntu) uses compiz. Maybe someone with more xfce knowledge would be better placed to hep you out

---

### Post by anotherdummhead on 2011-03-04
Nah i can't even find desktop effects (i know what you mean, i don't believe that KFCE uses them) i have Kubuntu on my other PC, it can really drain life out of a computer. Here i don't think that's the case, i don't think i messed up something during the instalation of all these drivers, but i still have those annoying trails :S

---

### Post by Hippytaff on 2011-03-04
Might it be something to do with the refresh rate...check out the display properties

---

### Post by anotherdummhead on 2011-03-04
60Hz, can't change, i think that's a little low, right ?

---

### Post by Hippytaff on 2011-03-04
Mine is 60Hz...I think that is fairly standard...this is what I would do. install another desktop effort (Gnome, Kde or if you need something light Lxde ICEwm) and see if the same thing happens...if not it's something to do with xfce, if so it might be an xorg issue.

Edit -> bear in mind I often do things the hard way and others might have an easier way to sort things :?

---

### Post by anotherdummhead on 2011-03-04
Hahahaha same here. Mate we have a problem there, i tried installing GNOME but it was somewhat closer to a disaster rather to a successful installation..In the end i removed half of my XFCE and reinstalled it all over again. I want the GNOME desktop, i just need a correct guide KFCE to GNOME, so can you find that for me ?

---

### Post by Hippytaff on 2011-03-04
Have a look at [this]("http://www.psychocats.net/ubuntu/puregnome")

---

### Post by anotherdummhead on 2011-03-04
> **Hippytaff said:**
> Have a look at [this]("http://www.psychocats.net/ubuntu/puregnome")

That's exactly what i've used and i almost erased whole Xubuntu :D needed to do a reinstall of the desktop..damn, maybe it's normal to see the trails ?

---

### Post by anotherdummhead on 2011-03-04
I tried the Ubuntu desktop now, even worse :S

---

