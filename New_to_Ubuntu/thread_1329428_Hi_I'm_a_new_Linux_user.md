---
title: "Hi I'm a new Linux user"
date: 2009-11-17
forum: New to Ubuntu
---

### Post by dj-skidz on 2009-11-17
Hello,
I'm new to using Linux.
 I have just tried to install drivers for my Nvidia Graphics card, but when ever i boot in to Ubuntu 9.10 i now get a message from my monitor saying unsupported.   I'm guessing that the resolution is now out of range for my monitor.  How can i change this.
Thanks
Skidz

---

### Post by halitech on 2009-11-17
press CTRL+ALT+F1 and log into the terminal and post the output of /etc/X11/xorg.conf

you probably need to add something like this
> SubSection "Display"
		Viewport   0 0
		Depth     24
		Modes    "1280x1024" "1440x1050"
	EndSubSection


change the numbers to match the max for your screen

---

### Post by ukripper on 2009-11-17
> **dj-skidz said:**
> Hello,
I'm new to using Linux.
 I have just tried to install drivers for my Nvidia Graphics card, but when ever i boot in to Ubuntu 9.10 i now get a message from my monitor saying unsupported.   I'm guessing that the resolution is now out of range for my monitor.  How can i change this.
Thanks
Skidz

Press CTRL + ALT+ F2. put your username and password and type below command:
```
xrandr
```

Post output here.

---

### Post by dj-skidz on 2009-11-17
Hi
Thanks for your quick reply.
Sorry for my ignorance, but do i have to type sudo sh /etc/X11/xorg.conf?
Skidz

---

### Post by nperry on 2009-11-17
> **dj-skidz said:**
> Hi
Thanks for your quick reply.
Sorry for my ignorance, but do i have to type sudo sh /etc/X11/xorg.conf?
Skidz

Hello there,

First of all welcome to Ubuntu.

If you just type into the terminal
```
cat /etc/X11/xorg.conf
``` and then copy the output into here with what monitor you have (+default resolution)

Thanks,
Neil Perry

---

### Post by dj-skidz on 2009-11-17
I have a 19" Logik Flatscreen monitor.
I can't post the whole read out, as i am typing this in a 2nd computer.

> SubSection "Screen"
Identifier "Screen0"
Device "Device0"
Monitor "Monitor0"
Default Depth 24
Subsection "Display"
		Depth     24
		Modes    "1600x1200" "1280x1024" "800x600" "640x480"
	EndSubSection 			 		
Thanks

---

### Post by ukripper on 2009-11-17
Can you run this command and post output here. It will give you horizontal and vertical refresh rate and then you can add it into xorg.conf

run this:
```
cvt 1600 1200 60
```

---

### Post by dj-skidz on 2009-11-17
> **ukripper said:**
> Can you run this command and post output here. It will give you horizontal and vertical refresh rate and then you can add it into xorg.conf

run this:
```
cvt 1600 1200 60
```

Result:

#1600x1200 59.87 Hz (cvt 1.93M3 hsync:74.54kHz; pclk: 161.00MHz
Modeline "1600x1200_60.00" 161.00 1600 1712 1880 2160  1200 1203 1207 1245 -hsync +vsync

Thanks

---

### Post by ukripper on 2009-11-17
> **dj-skidz said:**
> Result:

#1600x1200 59.87 Hz (cvt 1.93M3 hsync:74.54kHz; pclk: 161.00MHz
Modeline "1600x1200_60.00" 161.00 1600 1712 1880 2160  1200 1203 1207 1245 -hsync +vsync

Thanks

Here is your Horizontal refresh rate: 75
Vertical rate : 60

Now you need to add this in your xorg.conf:
```
sudo nano /etc/X11/xorg.conf
```

Now find Section "Monitor" and add below lines in bold under identifier:
> Section "Monitor"
        Identifier   "Monitor0"
        [B]HorizSync    49.0 - 74.0
        VertRefresh  60.0[/B]


save and exit.

reboot and see if it makes any difference.

---

### Post by dj-skidz on 2009-11-17
That has worked, thanks very much to everyone

---

### Post by ukripper on 2009-11-18
> **dj-skidz said:**
> That has worked, thanks very much to everyone

i am glad it worked for you. Can you make this thread Solved from Thread tools. Info in thti thread may be useful for someone.

---

