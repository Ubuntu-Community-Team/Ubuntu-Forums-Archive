---
title: "Nvidia Geforce GTS 360M driver error"
date: 2011-09-03
forum: New to Ubuntu
---

### Post by CorsairTrumpet on 2011-09-03
I have an Asus G60J with an Nvidia Gts 360M and when booting Ubuntu 11.04 after a flash of the bootsplash, the vid fails and i get white blocks.  I've seen some others with this issue but I can't find a solution.  Any help?

Thanks

---

### Post by CorsairTrumpet on 2011-09-03
bump

---

### Post by papibe on 2011-09-03
Try booting into safe mode and renaming the X Windows configuration file:
```
$ sudo mv /etc/X11/xorg.conf  /etc/X11/xorg.conf.old
```
And then reboot. If that does not work, try posting your X Windows log? It is this file:
```
/var/log/Xorg.0.log
```
BTW, if you boot into the 'blocks of white', try pressing Ctrl+Alt+F1 to get into text mode.
Regards.

---

### Post by CorsairTrumpet on 2011-09-03
I've been able to access terminal (via f1-f6) but I have no log for xorg....I've been trying all kinds of stuff so i might have messed things up more.  I've thought about just re-installing but I can't because when I attempt that I can't see the install screen.  what other out puts can i give you?

---

### Post by CorsairTrumpet on 2011-09-03
I've reinstalled xorg (really i sudo apt-get install ubuntu-desktop).  

the output of both your first request: mv cannot stat '/etc/x11/xorg.conf': no such file or directory.

the second -bash: /var/log/xorg.0.log: no such file or directory

---

### Post by papibe on 2011-09-03
Just to make sure, the config file is:
```
/etc/X11/xorg.conf
```
Note the capital X on X11.

The log is:
```
/var/log/Xorg.0.log
```
Note the capital X on Xorg.

Just double checking,
Regards.

---

### Post by CorsairTrumpet on 2011-09-03
okay, im sorry this may be more simple than i'm making it but here is where I stand:

I now can see/read the log file, but i cannot transfer the log file to the comp. i'm using to access the forums.  How can I, using only terminal, get the log file online? (note I'm familiar with terminal, but not to familiar. I've used Ubuntu for a while but mainly through a GUI)

Thanks again for all the help

---

### Post by CorsairTrumpet on 2011-09-04
okay here are some things I see in reading the log file:

no layout section. using the first screen section.
no screen section available. using defaults.
|-->screen "Default Screen Section" (0)
|   |--> Monitor "<default monitor>"
No monitor specified for screen "Default Screen Section".
Using a default monitor configuration.
...
...
usr/share/fonts/X11/cyrillic does not exsist
entry deleted from font path
"" "" "" ""/100dpi does not exist.
entry deleted from font path. (same for 75dpi at same location)

...
...
...
Nvidia GLX module 173.14.30
...
...
...
matched nvidia as auto configured driver 0
mantched nouveau as auto configured driver 1
"" nv as driver 2
"" vesa as driver 3
"" "" fbdev as driver 4
....
....
.....
Warning, counldn't open module nv
failed to load nv (module does not exist, 0)





hope some of this helps

---

### Post by CorsairTrumpet on 2011-09-04
"failed  to initialize the Nvidia graphics device!"  what? does that mean?  I know the card is good.  It ran Ubuntu 10.04 64 bit 2 weeks ago.

Also "No screens found" Which is odd because i'm reading it on a screen that its displaying on....

---

### Post by papibe on 2011-09-04
Try this:
```
$ sudo nvidia-xconfig
```
and then reboot, it may help to recreate a right xorg.conf.

BTW, Do you have any nvidia sticker that says [Optimus]("http://www.nvidia.com/object/optimus_technology.html")?

Regards.

---

### Post by blitzit on 2011-09-04
Have you installed proprietary NVIDIA drivers?

You would also need to blacklist some of the other stuff and completely remove some other NVIDIA stuff using apt-get before installing the drivers.

Done that already?

---

### Post by CorsairTrumpet on 2011-09-06
Did this. it wrote a new '/etc/X11/xorg.conf' file but still no luck on the reboot.


No sticker says Nvidia geforce gts 360 M Cuda 1GB.


lspci lists " nVidia Corp. gts215 [geforece gts 360M]
...
...
...
Kernel driver in use: nvidia
Kernel modules: nvidia-current, nvidia-173, nouveau, nvidiafb



Rao:

I believe i have the proprietary drivers installed.

What do I need to black list?

---

### Post by CorsairTrumpet on 2011-09-06
so It looks like I got it working.


after doing the following:

$ lspci 

I found that the drivers might have been interfering with one another.

I purged the Nvidia-173:  $ sudo apt-get purge nvidia-173

Now it seems to boot/run fine!


Thanks for all the help guys/ladies!

---

### Post by blitzit on 2011-09-07
That's exactly what I meant when I said you must remove all NVIDIA stuff that came with ubuntu through apt-get.

Although you already have your system working fine, I suppose there is no harm in having a look at this : [http://ubuntuforums.org/showthread.php?t=1838842](http://ubuntuforums.org/showthread.php?t=1838842). This is the standard way of doing it. There is also a mention of the blacklisting.

Cheers! :)

---

