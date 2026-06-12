---
title: "Intel display drivers for 4 Series"
date: 2009-01-06
forum: New to Ubuntu
---

### Post by risingpowers on 2009-01-06
Are there any Linux drivers for the Intel 4 Series chipset? Intel supposedly releases open source drivers, but I only find .exe files on their website and xserver-xorg-video-intel does nothing. This chipset has been been out for a few months now...do I just have to wait until drivers come out? Does anyone else have problems with this chipset on Ubuntu?

---

### Post by Titan8990 on 2009-01-06
Do the following:

hit CTRL+ALT+F1


log in using your username/pw


type the following commands:


```
sudo /etc/init.d/gdm stop
```
sudo dpkg-reconfigure xserver-xorg[/code]


Accept most of the default options as it will be what is already set at. When it asks you about graphics drivers select the Intel drives that best matches your chipset. 

Then restart graphics"

```
sudo /etc/init.d/gdm start
```

I assume by 4 series it is a G4x?

---

### Post by risingpowers on 2009-01-06
> **Titan8990 said:**
> Do the following:

hit CTRL+ALT+F1


log in using your username/pw


type the following commands:


```
sudo /etc/init.d/gdm stop
```
sudo dpkg-reconfigure xserver-xorg[/code]


Accept most of the default options as it will be what is already set at. When it asks you about graphics drivers select the Intel drives that best matches your chipset. 

Then restart graphics"

```
sudo /etc/init.d/gdm start
```

I assume by 4 series it is a G4x?

I don't believe so. I'll include some specific data in my next post.

---

### Post by risingpowers on 2009-01-06
First things first, after I typed those commands I did not recieve any prompt mentioning anything about drivers. I also have lost control of my mouse.

UPDATE: A restart solved this little problem.

---

### Post by risingpowers on 2009-01-06
```
zachary@zachary-ubuntu:~$ sudo xrandr -q
[sudo] password for zachary: 
Screen 0: minimum 640 x 480, current 800 x 600, maximum 800 x 600
default connected 800x600+0+0 0mm x 0mm
   800x600        61.0* 
   640x480        60.0  

```

```
zachary@zachary-ubuntu:~$ sudo lshw -C display
  *-display:0 UNCLAIMED   
       description: VGA compatible controller
       product: Mobile 4 Series Chipset Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 07
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm bus_master cap_list
       configuration: latency=0
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile 4 Series Chipset Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 07
       width: 64 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0

```

---

### Post by risingpowers on 2009-01-06
Shameful bump, will be back to the thread later since I have some errands to run.

---

### Post by risingpowers on 2009-01-06
Last bump, if no one replies I give up.

---

### Post by v1nsai on 2009-12-09
I'll bump this, I'm having trouble getting the display claimed too.

It's strange because I'm using compiz/emerald just fine, and awn is happily running without any problems, but cairo-dock has the black background around it when I try to enable opengl, which at first made me think it was a problem with cairo-dock but lshw -C display tells me that the display is unclaimed, which just makes me wonder why awn and compiz work o_0

I don't know if OP is still working on this problem, but I'd like to find a fix for this, it's not a big deal it's just kind of bothering me that I'm not getting the most out of my display.

---

