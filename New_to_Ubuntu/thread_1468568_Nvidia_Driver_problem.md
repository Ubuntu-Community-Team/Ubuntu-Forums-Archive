---
title: "Nvidia Driver problem"
date: 2010-05-01
forum: New to Ubuntu
---

### Post by EnderBG on 2010-05-01
Hi guys, I have a major issue with updating the driver for my Nvidia graphics card.  I am very new to ubuntu, love it so far, but i just have this one problem.  I am trying to update the driver(s) for my Nvidia GeForce 8200, just so i can do a bit of gaming and enable 3D effects on my laptop.  Problem is that every time I attempt to update it, right after the installation and reboot... I get a split screen of six tiles in horrible resolution.  At that point i attempted to uninstall the drivers, and nothing worked.  It was very difficult to work when the screen was split into six different pieces... so I just ended up reinstalling the OS to fix the issue.  Can anyone please tell me how I can get around this issue.... is it possible to fix it through a terminal window by typing in a bunch of commands? Please help... Im a total newb!  Thanks in advance guys.

INFO:  Ubuntu 10.04 LTS, Gnome 2.30, AMD Athlon Dual-Core QL-64, 3GB DDR2 RAM, GeForce 8200

---

### Post by wojox on 2010-05-01
You need to edit /etc/X11/xorg.conf and add this under Section "Device"

Option "ModeValidation" "NoTotalSizeCheck"

---

### Post by xumuk37 on 2010-05-01
and what about nVidia drivers? It affects me too...

---

### Post by wojox on 2010-05-01
> **xumuk37 said:**
> and what about nVidia drivers? It affects me too...

If you have six screens do the same.

---

### Post by xumuk37 on 2010-05-01
not the six screen. I'm talking about I either can install nVidia drivers, tried by Hardware Drivers and downloading from nVidia web (NVIDIA-Linux-x86_64-195.36.15-pkg2.run). It's always something wrong there... In Karmic and in Arch it works pretty fine! I'm thinking/sure it's a kernel problem, but don't know how to fix it... With 2.6.32-17-generic worked with no problems.

---

### Post by xumuk37 on 2010-05-01
bump!

---

### Post by wojox on 2010-05-01
> **xumuk37 said:**
> bump!

Have you looked at this thread [http://ubuntuforums.org/showthread.php?t=1467074&highlight=install+nvidia+driver](http://ubuntuforums.org/showthread.php?t=1467074&highlight=install+nvidia+driver)  ?

---

### Post by xumuk37 on 2010-05-01
> **wojox said:**
> Have you looked at this thread [http://ubuntuforums.org/showthread.php?t=1467074&highlight=install+nvidia+driver](http://ubuntuforums.org/showthread.php?t=1467074&highlight=install+nvidia+driver)  ?

Thanks a lot! This exactly what I get...

---

### Post by wojox on 2010-05-01
Your welcome.

---

### Post by EnderBG on 2010-05-01
> **wojox said:**
> You need to edit /etc/X11/xorg.conf and add this under Section "Device"

Option "ModeValidation" "NoTotalSizeCheck"

--- Where do I go to edit that file, is it done through the terminal window, or is there a GUI application for it or what?  Im sorry guys, im very new to ubuntu, typing commands in, etc, trying to learn as much as I can.  Can anyone give me step by step "idiot's guide" on how to do this... much appreciated!

---

### Post by wojox on 2010-05-01
Sure try:

```
gksudo gedit /etc/X11/xorg.conf
```

---

### Post by RyanBFS on 2010-05-01
gksudo gedit etc/x11/xorg.conf in your command line or navigate there using cd FOLDERNAME and cd .. to back up. then type sudo gedit FILENAME which will open the file in your text editor with root permissions.  Get used to navigating with command line because if your going to be editing xorg.conf theres a good chance that command line is what you'll be using on try 2 ;)

but be sure you back it up first!!!!

x11 is a very low level part of the linux GUI, in fact it's the "hardware meets software" that gnome or KDE rests on.  Little tweaks often do not result in what you are looking for.  To be honest, I've done hundreds of Ubuntu installs, and while I don't consider my self an expert or anything, it's been a long time since I've had to mess with x11.  Back in 7.XX and prior it was very common, but I think there are some new drivers for Nvidia this release... it's not uncommon for a new driver to require a bit of debugging even after it's out.

---

### Post by EnderBG on 2010-05-01
Ok guys, I installed the driver (again), and when i rebooted i got the same 6 tiles..... i opened a terminal and typed in the : gksudo gedit /etc/x11/xorg.conf  ... and i got an error message saying: (gksudo: 1410): Gtk-WARNING **: cannot open display:

..... so now im left having to do it with just the terminal ... (Ctrl+Alt+F1)
Can anyone give me an exact list of commands i can input in order to fix this issue..... through the terminal.... thanks again (sorry for my ignorance):confused:

---

### Post by EnderBG on 2010-05-01
bump

---

### Post by xumuk37 on 2010-05-01
I guess you'll have to wait untill tomorrow... It' too late now. Do "bump" tommorow morning xD.

While you can take a look in System > Preferences > NVIDIA X Server Settings, may be you find something there

---

### Post by xumuk37 on 2010-05-01
bump

---

### Post by 3rdalbum on 2010-05-01
> **EnderBG said:**
> Ok guys, I installed the driver (again), and when i rebooted i got the same 6 tiles..... i opened a terminal and typed in the : gksudo gedit /etc/x11/xorg.conf  ... and i got an error message saying: (gksudo: 1410): Gtk-WARNING **: cannot open display:

I'm guessing you hit Control-Alt-F1 (or similar) to get to a terminal... if you have, then use:

```
sudo nano /etc/X11/xorg.conf
```

---

### Post by EnderBG on 2010-05-02
Well guys I am yet again reinstalling the OS.... and this time I'll attempt to install the driver manually from the Nvidia official website following this guide  \/  \/  \/

[http://www.ubuntugeek.com/howto-install-nvidia-drivers-manually-on-ubuntu-10-04-lucid-lynx.html](http://www.ubuntugeek.com/howto-install-nvidia-drivers-manually-on-ubuntu-10-04-lucid-lynx.html)

Ill post if there is any progress on fixing this problem.  If anyone has any additional suggestions please feel free to post as I will be checking back here for answers if this next experiment fails. :shock:

---

### Post by sadaruwan12 on 2010-05-02
It's stated that Lynx have some problems with the nVidia drivers in there official release notes try the ones from the repo's or use the binary packages that you can get from hardware drivers at System -> Administration.

---

### Post by EnderBG on 2010-05-02
> **sadaruwan12 said:**
> It's stated that Lynx have some problems with the nVidia drivers in there official release notes try the ones from the repo's or use the binary packages that you can get from hardware drivers at System -> Administration.

--- I've tried installing the drivers through that, and that was my initial problem.  Every time I got to system/admin/hardware drivers ...... the driver installs..... i reboot.... and i get 6 screens on my monitor???????

---

### Post by 23dornot23d on 2010-05-02
I just did a kernel upgrade after loading the latest Nvidia Drivers and fixed some issues that I was having ..... 
here is the last post I made on the Nvidia Thread explaining what I did .... hope that this helps ....

Make sure that you do a full upgrade of the latest packages .... 

I used Update Manager ..... to make sure everything was up to date ....

[http://ubuntuforums.org/showthread.php?p=9217202#post9217202](http://ubuntuforums.org/showthread.php?p=9217202#post9217202)

Might be worth a try if nothing else is working .....

I still seem to have a problem with console mode .... but it does not do the same thing on each boot ....
I can now switch into console mode again .... Alt+Ctrl+F1 ..... Alt+Ctrl+F7 to return to normal graphical
Desktop works ok now .....

---

