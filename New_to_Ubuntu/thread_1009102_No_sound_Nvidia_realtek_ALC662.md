---
title: "No sound Nvidia realtek ALC662"
date: 2008-12-12
forum: New to Ubuntu
---

### Post by dgtlkttn on 2008-12-12
Hi there,
I am at a loss with sound at the moment, fresh install of ubuntu 8.10, no sound, no idea where to get drivers, I have asla mixer and have checked all volume levels and have followed the comprehensive guide and still nothing.  Below is the output from aplay-l




```
digitalkitten@digitalkitten:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC662 Analog [ALC662 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC662 Digital [ALC662 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```


Can anyone please offer a solution? I am now running with restricted drivers for graphics as well as the flickering screen was just too much.

Thanks for your time :)

---

### Post by sickman666 on 2008-12-12
I too have this same problem...fresh install,no sound. I tried to see if it was on the actual boot cd but not that i can find. I found the right driver by going to the gateway website(gateway 7305) and down loading the driver but i dont know how to install the damn thing. If i figure it out i will let you know what i did so maybe we can enjoy the finer things in life....like SOUND with or games and movies.:confused::mad:

---

### Post by dgtlkttn on 2008-12-12
> **sickman666 said:**
> I too have this same problem...fresh install,no sound. I tried to see if it was on the actual boot cd but not that i can find. I found the right driver by going to the gateway website(gateway 7305) and down loading the driver but i dont know how to install the damn thing. If i figure it out i will let you know what i did so maybe we can enjoy the finer things in life....like SOUND with or games and movies.:confused::mad:

Hi sickman,

Yep, I'm finding it quite hard to get my head round how things work within linux as a whole. 

I have no idea how to install the driver either, should I actually know where it is... searching hasn't yielded any results.

If I find out anything i'll post back here too ok? :)

---

### Post by tomtom1982 on 2008-12-12
Please try to add the following line to the /etc/modprobe.d/options file :
```
options snd-hda-intel model=laptop
```

---

### Post by dgtlkttn on 2008-12-12
> **tomtom1982 said:**
> Please try to add the following line to the /etc/modprobe.d/options file :
```
options snd-hda-intel model=laptop
```

ok, before I do that... Why laptop? I'm running a pc



-------------

...right I've tried anyway, and it won't let me save it. :confused:

---

### Post by airblad3 on 2009-06-07
I'm having the same problem with this, When i list it with lspci it shows but i get no sound.
Using Kubuntu 9.04

---

### Post by manjusri on 2009-06-08
go to searh realtek alc662.thereis a kink to download the driver.but its not simple on ubuntu .for pc or fedora it's automatic):P

---

### Post by manjusri on 2009-06-08
excuse;search realtek alc662in the forum there is a link to downoad the driver .for ubuntu it's notsimple; but for pc or fedora it'automatic

---

