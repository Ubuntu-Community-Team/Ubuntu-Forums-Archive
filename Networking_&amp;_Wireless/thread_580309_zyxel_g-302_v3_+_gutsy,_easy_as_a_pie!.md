---
title: "zyxel g-302 v3 + gutsy, easy as a pie!"
date: 2007-10-18
forum: Networking &amp; Wireless
---

### Post by m_bridge on 2007-10-18
On a fresh gutsy install, i just got my zyxel g-302 v3 to work in less than 10 minutes!
here's how to do it

initially ubuntu loads the r8180 module, you can verify this with 
```
$ lsmod |grep 818
```
this module freezed my kernel two times when trying to set the wep key with iwconfig so i decided to try with ndiswrapper
[U]
1. remove the current module[/U]
```
$ sudo rmmod r8180
$ gksudo gedit /etc/modprobe.d/blacklist
```
add this line at the bottom 
```
blacklist r8180
```
reboot the computer and make sure the module is not loaded with
```
$ lsmod |grep 818
```
(should not list the module anymore)

_2. install ndiswrapper_
install ndiswrapper-utils with synaptic or typing
```
$ sudo apt-get install ndiswrapper-utils-1.9
```

_3. install the window driver_
the drivers from the bundled cd are working fine for me
insert the cd and copy the folder Drivers/WINXP to the desktop
install with
```
ndiswrapper -i Desktop/WINXP/net8185.inf
```

at this point with 
```
$ ndiswrapper -l
i get 

```
```
net8185 : driver installed
        device (10EC:8185) present (alternate driver: r8180)

```
[U]
4. load ndiswrapper module[/U]
```
$ sudo depmod -a
```
and if there's no error
```
$ sudo modprobe ndiswrapper
```

_5. configure the network with nm-applet_
i tried to configure the essid manually with iwconfig but it didn't work (same problem back with edgy)
but the nm-applet seems to do the job well. in fact if everything went fine
you should see the nm-applet icon flashing on the top right of your screen, next to the clock
click it and setting up your wireless should be matter of few clicks
(in my case is working well with a 128-bit ASCII key)

_6. save the changes_
if your card is working you probably want to save this setup for the next time you reboot, to do so type
```
$ sudo ndiswrapper -m
$ gksudo gedit /etc/modules
```
add the line "ndiswrapper"

_7. reboot_ and it should be working again after the restart

never been so easy for me:guitar:!

---

### Post by imopen on 2007-10-19
Tonight to make my card (Realtek RT8180L) work I did the same thing :o

I blacklisted r8180, which cause kernel panic on startup when configured on WEP, and I installed ndiswrapper :mrgreen:

Telepathy :lolflag:

---

### Post by ajm8127 on 2007-10-21
This works great. Rock on! :guitar:

---

### Post by Pitak on 2007-10-22
_3. install the window driver_
the drivers from the bundled cd are working fine for me
insert the cd and copy the folder Drivers/WINXP to the desktop
install with
```
ndiswrapper -i Desktop/WINXP/net8185.inf
```

I get an error at this point in the terminal saying "This file does not have permissions on line 152"

---

### Post by jocku on 2007-10-23
:-({|=
JEAH, Thak You!

---

### Post by Pitak on 2007-10-24
bump.

---

### Post by Aathos on 2007-11-07
Hey, that's a great how-to.  I was just in the process of writing one when I found it.  The directions here should apply to the rtl8180 and rtl8187 chipsets as well.  

However, I have found that sometimes ndiswrapper does not automatically detect the card.  In that case you have to use
```
lspci -nn
``` to find the device id.  Look for a line that looks something like:
```
02:09.0 Ethernet controller [0200]: Belkin Wireless PCI Card - F5D6001 [1799:6001] (rev 20)
```
in my case the device id is: 1799:6001.  Yours may be different.  Then type 
```
sudo ndiswrapper -a 1799:6001 net8185
``` But of course use your device id, not mine.

 BTW, if you use the download the drivers, the name is net8180.  They can be found [here.]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=5&PFid=5&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true#RTL8180L") You can download any of the version 1.73 windows drivers.  Make sure you extract both the .ini and .sys files to the same place.

---

### Post by duojet on 2007-11-08
YES! this is the best solution I've seen yet!

P.S. I got the "line 152" error as well, but running the same command with "sudo" in front fixed that.

---

### Post by lcl on 2007-11-12
I have a trendnet TEW-228PI, I downloaded from realtek the NET8180.INF and followed the instructions here and it worked.  Thank you all.

---

### Post by elfed on 2007-12-03
Wonderful!  Many thanks as this has done the trick!  I was just about to give up on my first ever Ubuntu install as I've been trying for about 2 months to get this card working - could get it to work without security but not with WPA turned on.  Will now get another of these cards to build a second Ubuntu machine for my wife!  I have an all ZyXEL wireless network that has worked without any glitches for the last couple of years.

---

### Post by Uppsala9496 on 2007-12-03
I tried this guide in the 32 bit version of Gutsy and everything worked fine.

Conversely, I tried this in the 64 bit version and it does not work.  The driver is listed, however it doesn't look like it recognizes the wireless card.

Anyone know if this is due to the driver not working correctly in the 64 bit version (says the driver is installed)?

I want the 64bit version so I can run the SMP client for Folding@Home.

](*,)

---

### Post by Uppsala9496 on 2007-12-08
BUMP:

ndiswrapper -l returns:

net8185 : driver installed
device (10EC:8185) present (alternate driver: r8180)

iwconfig shows:

lo no wireless extensions
eth0 no wireless extensions

I loaded the WINXP drivers from the cd that came with my card.  The website shows some linux drivers, but I have no idea how to install the .tar.gz files from it.

---

### Post by James Thayer on 2008-01-29
I followed this exact guide but when I get to the part where I have to type my WEP key, then I click Login, it just crashes my computer :confused:
What can be causing that? It's really starting to get on my nerves.

---

### Post by jel0327 on 2008-02-27
I installed the 8185 WinXP driver befor blacklisting the 8180 driver and I still had problems.  This was before I found this post.  Removing and blacklisting the 8180 driver and rebooting finished my problem.  
Well Done Boss

---

### Post by Yucleto on 2008-02-27
Hey,

It worked, then restart and stop working, i tried to redo the steps no success no more wifi access

hope you could help.

Regards !

---

