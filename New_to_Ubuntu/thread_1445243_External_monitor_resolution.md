---
title: "External monitor resolution"
date: 2010-04-02
forum: New to Ubuntu
---

### Post by Prescott.Dale.AP on 2010-04-02
I have a Tv hooked up as an external monitor to my samsung netbook. On dual boot xp it works fine in a 1024 x 800 .... or 1024 x 764 I can't remember exactly which. But on ubuntu 9.10 it seems to stay at 800 x 600 (in display options there is no higher res' available), which is pretty bad on a netbook because everything on the screen is massive. I know the monitor can do higher resolutions and my netbook can, so its definitely ubuntu thats the problem

I've looked through some other forum posts about this because a lot of people have the same problem, but I don't understand any of it tbh... xorg files nd using terminal etc then they mention menus in admin that I don't even have. Bottomline is I'm a newbie to ubuntu, I've had it for a while and I love the simplicity, but when it goes wrong I'm a dummie and have no idea... I normally reinstall it when it does because I can't do anything. 

If someone can explain to me how to set to a higher resolution for my monitor in retard terms then  it would be much appreciated. Thanks

---

### Post by Elfy on 2010-04-02
IT might help to know what graphics card you have - if you are not sure, run ```
lspci
``` and paste the output.

---

### Post by Prescott.Dale.AP on 2010-04-02
dale@dale-mini:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)
03:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller (rev 13)

---

### Post by Prescott.Dale.AP on 2010-04-02
hope thats the right thing.... you don't need to know the monitor or laptop specs do you? just say if needed

---

### Post by soumo on 2010-05-26
Hi! Exact same problem as you though different netbook, same driver.
Did you find a solution?

xorg.conf is no longer used in Lucid (I think), and is nowhere to be found in my system.  Can you check /etc/X11/ and /root/ to see if you have it?

---

### Post by soumo on 2010-05-26
Okay, so following here:
[http://ubuntuforums.org/showthread.php?t=1305919&page=1](http://ubuntuforums.org/showthread.php?t=1305919&page=1)

I have a workaround that may be of use to you.

1. plug in external display BEFORE booting up
2. if that does not do it, type in 'sudo xrandr' which will give you all the display modes available for your current driver for each device:

```
home@vortex:~$ xrandr
Screen 0: minimum 320 x 200, current 1360 x 768, maximum 4096 x 4096
VGA1 connected 1360x768+0+0 (normal left inverted right x axis y axis) 1600mm x 900mm
   1360x768       60.0*+
   1280x768       59.9  
   1024x768       60.0  
   800x600        60.3  
   640x480        60.0     59.9  
   720x400        70.1  
LVDS1 connected (normal left inverted right x axis y axis)
   1024x600       60.0 +
   800x600        85.1     72.2     75.0     60.3     56.2  
   640x480        85.0     72.8     75.0     59.9  
   720x400        85.0  
   640x400        85.1  
   640x350        85.1  

```

3. So in my case my monitor is VGA1.  I typed:
```
xrandr --auto --output VGA1 --mode 1360x768
```

which did the trick!  You can independently set the laptop as well. 


OR

If you just want the external display and no laptop, I went into monitors, enabled external monitor, then disabled laptop by clicking on it then shutting off.  This allowed me to increase resolution on the monitor.

Hope this helps!  Next step is to get compiz working with a window decorator.

---

