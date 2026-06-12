---
title: "matrox g400 problems"
date: 2011-08-20
forum: New to Ubuntu
---

### Post by chewycwook on 2011-08-20
Hello, I recently installed ubuntu 11.04 and it is only detecting one of my monitors.  One remains blank, the computer is acting as if I only have one. I have tried to download the matrox drivers but i get the following errors:

jason@jason-Precision:~/Desktop/matrox_driver-x86_32-4.4.0$ sudo sh install.sh
[: 43: i686: unexpected operator
install.sh: 57: function: not found
install.sh: 69: function: not found
install.sh: 78: function: not found
install.sh: 95: function: not found

Please enter the full path to your current X11R6 directory: 
Example: /usr/X11R6


Type of video card:
jason@jason-Precision:~/Desktop/matrox_driver-x86_32-4.4.0$ sudo lspci | grep VGA01:00.0 VGA compatible controller: Matrox Graphics, Inc. MGA G400/G450 (rev 04)
jason@jason-Precision:~/Desktop/matrox_driver-x86_32-4.4.0$ 


I have the latest MGA drivers:
jason@jason-Precision:/etc/X11$ sudo apt-get install xserver-xorg-video-mga
Reading package lists... Done
Building dependency tree       
Reading state information... Done
xserver-xorg-video-mga is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
jason@jason-Precision:/etc/X11$ 

I recently bought the card and switched which computer I am going to use solely for the purpose of having dual monitors, I have gotten everything done except for that. 
I have included as much info as i thought to, If you need anything else I will gladly provide it and thank you for your help in advance.

---

### Post by blazemore on 2011-08-22
> **chewycwook said:**
> Hello, I recently installed ubuntu 11.04 and it is only detecting one of my monitors.  One remains blank, the computer is acting as if I only have one. I have tried to download the matrox drivers but i get the following errors:

jason@jason-Precision:~/Desktop/matrox_driver-x86_32-4.4.0$ sudo sh install.sh
[: 43: i686: unexpected operator
install.sh: 57: function: not found
install.sh: 69: function: not found
install.sh: 78: function: not found
install.sh: 95: function: not found

Please enter the full path to your current X11R6 directory: 
Example: /usr/X11R6


Type of video card:
jason@jason-Precision:~/Desktop/matrox_driver-x86_32-4.4.0$ sudo lspci | grep VGA01:00.0 VGA compatible controller: Matrox Graphics, Inc. MGA G400/G450 (rev 04)
jason@jason-Precision:~/Desktop/matrox_driver-x86_32-4.4.0$ 


I have the latest MGA drivers:
jason@jason-Precision:/etc/X11$ sudo apt-get install xserver-xorg-video-mga
Reading package lists... Done
Building dependency tree       
Reading state information... Done
xserver-xorg-video-mga is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
jason@jason-Precision:/etc/X11$ 

I recently bought the card and switched which computer I am going to use solely for the purpose of having dual monitors, I have gotten everything done except for that. 
I have included as much info as i thought to, If you need anything else I will gladly provide it and thank you for your help in advance.


Try
```
chmod +x install.sh
sudo ./install.sh
```

---

### Post by Wim Sturkenboom on 2011-08-22
I guess that the driver that you're trying to install is a very old driver. I remember (;)) X11R6 from the days of RedHat 8.0 (released in september 2002).

I think that you have to modify a number of lines in that script to get it going. And I'm wondering if it's the way to go if Ubuntu has a driver available.

---

### Post by realzippy on 2011-08-22
+1 to wim.

This driver will not work on actual Xservers.
Shame they don't mention this on their download page.

To get started,you could post output from

```
xrandr -q
```

and your

/var/log/Xorg.0.log file  (attach,it is pretty long)

---

### Post by chewycwook on 2011-08-22
jason@jason-Precision:~$ xrandr -q
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 400 x 300, current 1024 x 768, maximum 1024 x 768
default connected 1024x768+0+0 0mm x 0mm
   1024x768       75.0*    70.0     60.0  
   832x624        75.0  
   800x600        75.0     72.0     60.0     56.0  
   720x450        60.0  
   640x480        75.0     73.0     67.0     60.0  
   720x400        70.0  
   680x384        60.0  
   576x432        60.0  
   512x384        75.0     70.0     60.0  
   416x312        75.0  
   400x300        75.0     72.0     60.0     56.0  

Thank you!  The other file should be attached.
I have a card with two DVI plugs and am thinking about buying vga adapters, I would assume that would be newer, thus better support if this is not do-able.

---

### Post by realzippy on 2011-08-22
No idea.
Matrox (mga) kernel module/driver loaded successfully,
an Acer monitor recognised... 

Is it an AGP card?

---

### Post by chewycwook on 2011-08-22
Yes it is AGP

---

### Post by realzippy on 2011-08-22
..which version of xserver-xorg-video-mga do you run?

Tried the latest from [xorgedgers]("https://launchpad.net/~xorg-edgers/+archive/ppa/+index?batch=75&direction=backwards&memo=300&start=225") (1.4.13.) ?

---

### Post by chewycwook on 2011-08-22
jason@jason-Precision:~$ aptitude show xserver-xorg-video-mga
Package: xserver-xorg-video-mga          
State: installed
Automatically installed: no
Version: 1:1.4.13.dfsg-3build1
Priority: optional
Section: x11
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Uncompressed Size: 246 k
Depends: libc6 (>= 2.7), xorg-video-abi-10, xserver-xorg-core (>=
         2:1.10.0-0ubuntu1~)
Suggests: firmware-linux
Provides: xorg-driver-video
Description: X.Org X server -- MGA display driver
 This package provides the driver for the Matrox MGA family of chipsets,
 including Matrox Millennium and Mystique cards. 
 
 More information about X.Org can be found at: <URL:http://www.X.org> 
 
 This package is built from the X.org xf86-video-mga driver module.




Appears to already be 1.4.13

---

### Post by realzippy on 2011-08-22
So I have no idea.
There is a package you might want to install:
matroxset

[I]This utility can be used to map heads to outputs, change the output
mode to monitor, TV, or digital flat panel, display information about
horizontal and vertical blanking, and view or modify a number of card
specific controls.[/I]

maybe it helps.

Do you have an old ubuntu version you could start in live mode
to see if both monitors a recognized?

---

### Post by chewycwook on 2011-08-22
matroxset looks promising but it is looking for the frame buffer:

       -f DEVICE
           Manipulate the frame buffer DEVICE (default is /dev/fb1).


jason@jason-Precision:~$ matroxset 
Cannot open /dev/fb1: No such file or directory


What is the location of the frame buffer that I am looking for?

---

### Post by realzippy on 2011-08-23
Afaik the default fb (if using 1 graphics device) is fb0,
don 't know why matroxset looks for fb1 as default...?
..otherwise,the lack of fb1 might be a hint for not finding 2nd monitor.

```
me@mine:~$ matroxset -h
usage: matroxset [-f fbdev] [-o output] [-m] [value]

where -f fbdev  is fbdev device (default /dev/fb1)
      -o output is output number to investigate (0=primary, 1=secondary=default)
      -m        says that CRTC->output mapping should be changed/retrieved
      -p        print information about blanking
      -l        list controls
      -c        get/set control value
      -e        edit controls (interactively)
      value     if present, value is set, if missing, value is retrieved

```

So you might try:
```
sudo matroxset -f /dev/fb0
```

Read:
[http://www.mjmwired.net/kernel/Documentation/fb/framebuffer.txt](http://www.mjmwired.net/kernel/Documentation/fb/framebuffer.txt)
[http://manpages.ubuntu.com/manpages/lucid/man1/matroxset.1.html](http://manpages.ubuntu.com/manpages/lucid/man1/matroxset.1.html)
[http://directfb.org/wiki/index.php/Matrox_G400_Dual_Head](http://directfb.org/wiki/index.php/Matrox_G400_Dual_Head) (pretty old)

Can't help you with matroxset since it refuses to run with non-matrox cards.

---

### Post by chewycwook on 2011-08-23
jason@jason-Precision:~$ sudo matroxset -f /dev/fb0
ioctl failed: Inappropriate ioctl for device


Does this lead you to any clues about anything?  I'm thinking the options are about out.  Thank you for your efforts!

---

### Post by realzippy on 2011-08-23
I googled a little about g400,dual view.
It looks bad.
Eg here,post is from 2011:
[http://forum.tuxx-home.at/viewtopic.php?f=1&t=1300](http://forum.tuxx-home.at/viewtopic.php?f=1&t=1300)

In that matrox forum there are a few threads with your problem,
also with older ubuntu versions.
Maybe you could find a solution running 6.10 and that old matrox driver
mentioned in a few threads there,but this would lack online security.
I am sorry,but I cannot help you.

---

