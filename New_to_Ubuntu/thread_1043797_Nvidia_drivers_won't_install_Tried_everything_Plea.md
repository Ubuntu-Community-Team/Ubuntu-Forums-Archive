---
title: "Nvidia drivers won't install Tried everything Please help"
date: 2009-01-18
forum: New to Ubuntu
---

### Post by waynefwayne on 2009-01-18
I am trying to install nvidia driver for a GeForce 6100
I have used ubuntu's auto install and envyng-core
Installed driver version 177 and 173
every time I get a black screen on restart.

---

### Post by pytheas22 on 2009-01-18
I can't promise that I can help, but if you post the output of these commands, I'll try:
```

lspci -nn
uname -rm
```

Also, at which point exactly do you get the black screen?  Is it before the big orange Ubuntu bar even appears, before the login screen or after you enter your username and password to log into Gnome?  If you press control-alt-backspace at the blackscreen, what happens?  If you press control-alt-F1, what happens?

Google seems to think the Geforce 6100 is supported by nvidia-glx-new, so it should work.

---

### Post by stoogiebuncho on 2009-01-18
I found good help here:

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia")

This is what solved it for me: 

> Screen Blanks/Monitor Turns Off

Using a laptop with a GeForce Go card, or connecting the sole display via DVI on a dual-head system sometimes results in the screen not receiving a picture. This is caused by the driver outputting video to the VGA port on the graphics card, instead of DVI.

The usual hint that you have this problem is when you hear the startup sound but nothing appears on the screen. If you do not hear any sound, you are more than likely experiencing unrelated problems.

This is a launchpad bug about displays on digital outputs being blank when using NVIDIA binary driver, and can be resolved by editing your /etc/X11/xorg.conf file:

*

Switch to the console (Try using ctrl+alt+F1, or reboot and select recovery mode from the GRUB menu.)
*

Use your text editor to open /etc/X11/xorg.conf. (try sudo nano /etc/X11/xorg.conf)
*

Find the line that says Section "Screen"
*

Insert a new line that says Option "UseDisplayDevice" "DFP".
*

Save the file. If you had to restart into recovery mode, type reboot, otherwise restart your display using sudo /etc/init.d/gdm restart.

---

### Post by mjheagle8 on 2009-01-18
did you try installing the drivers using envyng? that is a very good and helpful utility for installing nvidia drivers.

---

### Post by waynefwayne on 2009-01-19
Pytheas22
when type in unsme -rm I get 2.627-9-generic i686
what part of lspci -nn did you need?

---

### Post by hyper_ch on 2009-01-19
You could install the proprietary nVidia drivers... I'd suggest th 180.18 drivers there

(1) Download the drivers:
32-bit [ftp://download.nvidia.com/XFree86/Linux-x86/180.18/NVIDIA-Linux-x86-180.18-pkg1.run](ftp://download.nvidia.com/XFree86/Linux-x86/180.18/NVIDIA-Linux-x86-180.18-pkg1.run)
64-bit [ftp://download.nvidia.com/XFree86/Linux-x86_64/180.18/NVIDIA-Linux-x86_64-180.18-pkg2.run](ftp://download.nvidia.com/XFree86/Linux-x86_64/180.18/NVIDIA-Linux-x86_64-180.18-pkg2.run)

(2) make the file executable

(3) log out of your session

(4) start a terminal while logged out
```

cttrl-alt-f3

```

(5) uninstall the nvidia drivers you have
```

sudo apt-get remove --purge nvidia/*

```

That should remove multiple things - if unsure post here first what it removes

(6) go to the place where you downloaded the new drivers and start installation
[code]
sudo ./NV......
[/cod]

(7) reboot

---

### Post by pytheas22 on 2009-01-19
> Pytheas22
when type in unsme -rm I get 2.627-9-generic i686
what part of lspci -nn did you need?

I would want to see the line from 'lspci -nn' that describes your video card.  It should mention something like 'VGA controller' or 'Video device'.

Also, try what hyper_ch suggests above.  It may work.  Note however that step 4 of his instructions should read:
> 
(4) start a terminal while logged out by pressing 'control-alt-F3'

alt-F3 alone won't do anything...I guess that was just a typo.

---

### Post by hyper_ch on 2009-01-19
*fixed*

---

### Post by waynefwayne on 2009-01-19
I eresed all nvidia drivers 
I dont know what he means by another terminal
Ill have the other info in a second
thanks for the help

---

### Post by waynefwayne on 2009-01-19
I cant see a vga or video but when Input
lspci | grep vga i recive
vga compatible controller: nvidia corporation c51g [Geforce 6100]
(rev a 2)

---

### Post by pytheas22 on 2009-01-19
Try this (basically these are just hyper_ch's instructions, but translated to bash commands as far as possible):

1. log out of the desktop
2. at the login screen, press control-alt-F3.  This will bring you to a command prompt.  Log in there with your normal username and password.
3. run these commands at the prompt:

```
sudo /etc/init.d/gdm stop
wget ftp://download.nvidia.com/XFree86/Linux-x86/180.18/NVIDIA-Linux-x86-180.18-pkg1.run
sudo apt-get install build-essential
sudo chmod +x NVIDIA-Linux-x86-180.18-pkg1.run
sudo ./NVIDIA-Linux-x86-180.18-pkg1.run
```

Follow the instructions on the screen to build the new nvidia driver.  When you're done, reboot the computer by typing:
```

sudo shutdown -r now
```

Do things work better after a reboot?

If you get any error messages at any point, please try to copy them here as exactly as possible.

---

### Post by waynefwayne on 2009-01-19
I get the black screen again? 
Thanks for trying

---

### Post by pytheas22 on 2009-01-19
> I get the black screen again?
Thanks for trying 

Did all the commands run successfully?  Are you sure the nvidia driver was built?

Also, what is the output of:
```

lspci -nn | grep -i geforce
```

---

