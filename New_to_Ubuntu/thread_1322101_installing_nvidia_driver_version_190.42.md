---
title: "installing nvidia driver version 190.42"
date: 2009-11-10
forum: New to Ubuntu
---

### Post by medya on 2009-11-10
Hey guys I saw the website of nividia that their latest version is 190.42 
in the ubuntu app for installing hardware driver it says the latest recmomended version is 185.

why 190.42 is not included in ubuntu 9.10 ?
and should I install 190.42 by myself ?

---

### Post by TheBuzzSaw on 2009-11-10
The version 185 is plenty reliable. It is what I use. I have attempted installing the latest versions, and it usually does nothing except break my display. Ignore the "latest" versions unless you *really* know what you are doing (and can recover from major disasters).

---

### Post by ratcheer on 2009-11-10
I am using 190.42 with no issues at all. Go for it, if you want to.

Tim

---

### Post by medya on 2009-11-10
> **ratcheer said:**
> I am using 190.42 with no issues at all. Go for it, if you want to.

Tim

how did u install it, did u use .Bin file or there is a deb package for it.
I rather ubuntu officialy make the update . because my current nvidia has bugs with Compiz Cube perhaps it is fixed in 190.42 ??

---

### Post by ratcheer on 2009-11-10
I installed it from the .run file from the nVidia web site. I am using the Compiz cube, as well. If you decide you want to try it, here is how to install it:

```

Ctrl-Alt-F1

cd to directory where .run file resides

sudo /etc/init.d/gdm stop

sudo sh ./NVIDIA-Linux-x86-190.42-pkg1.run

When the question is presented, choose the xorg auto configuration option

sudo reboot

```Tim

---

### Post by Mariane on 2009-11-10
When I tried it said "The nvidia smart scan does not support your system at this time". 

How can I get nvidia driver, please? ANY nvidia driver... 

Mariane

---

### Post by ratcheer on 2009-11-10
Go to [http://www.nvidia.com](http://www.nvidia.com) and go to the Download Drivers link near the top left. Select the proper options to define your card and system.

Tim

---

### Post by Mariane on 2009-11-10
OK, I didn't write my question precisely enough. 
I mean I have no idea what driver I need. It used to be detected automatically, now I don't know if it's 1200x1400 or 1100x 1600 or whatever... 

Mariane

---

### Post by ratcheer on 2009-11-11
Sorry. That depends on a couple of things. What size monitor are you using? What nVidia graphics card are you using? You should also need to know the recommended refresh rate of your monitor.

If you have the manual for your monitor, there should be recommended resolution and refresh rate published in it. If not, maybe you can find it on the manufacturer's web site.

Or, maybe your nVidia card really is too old for this driver, in which case you should go back to the driver that comes with Ubuntu, like TheBuzzSaw said.

Tim

---

### Post by k.abel on 2009-11-11
I was experiencing some very sluggish desktop performance with Kubuntu 9.10 until I upgraded to the 190 drivers.  NVidia 8800 series card, two monitors.

I was lazy and did it all from repositories: [http://www.ubuntugeek.com/install-nvidia-graphics-drivers-190-42-in-ubuntu-karmicjauntyintrepidhardy.html](http://www.ubuntugeek.com/install-nvidia-graphics-drivers-190-42-in-ubuntu-karmicjauntyintrepidhardy.html) 

As soon as I restarted X (actually rebooted the entire system for the heck of it) all the problems disappeared.  Desktop switching was a lot more responsive, no redraw lag when I moved or resized windows, load avg is down (which surprised me).

ETA: I was using the 185 drivers from the main repos beforehand.

---

### Post by Zoot7 on 2009-11-11
I too am using the 190.42 driver with my laptops 8600M GT. No issues here at all. But as a rule of thumb you're better off to install the driver Ubuntu recommends.

---

### Post by Mariane on 2009-11-12
> **Zoot7 said:**
> I too am using the 190.42 driver with my laptops 8600M GT. No issues here at all. But as a rule of thumb you're better off to install the driver Ubuntu recommends.

Absolutely! And I would say more, if it works, don't touch it! Unless you enjoy flipping a coin, head it works, tail your computer is unusable and you're in for days of fiddling. 

There are problems with 9.10 and nvidia drivers. 

Mariane

---

