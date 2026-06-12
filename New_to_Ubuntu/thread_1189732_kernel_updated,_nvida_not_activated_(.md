---
title: "kernel updated, nvida not activated :("
date: 2009-06-17
forum: New to Ubuntu
---

### Post by super kim on 2009-06-17
Hi, i have been suffering under the opressive rule of microsoft for too long now, so a few months ago installed ubuntu 8.10 with the wubi installer. i really liked the os and found it worked so much better than vista! so i decided to create an ext3 partition and give ubuntu its own space as it were. everything was sweet :)

Then i updated to ubuntu 9.04 jaunty jackalope. i didnt notice much difference except the system would completely crash, infrequently and for no apparent reason. i have managed to continue using ubuntu despite the total system faliures every now and then. 

Untill today, so i read on this very forum how others had the same problem. and i read that there was a fix for the bug. i was so excited i hurried to open my terminal and abbra kaddabra i have a shiny new updated kernel.
well its really too soon to know if the fix has worked for me but fingers crossed hey, got to be optimistic with these types of things you know!

Anyyway i rebooted and instantly had problems, i was tired from being up too long and missed the error as it flashed before my eyes, but no matter i was presented with many more, and these required me to click.

The problem was with the display settings, and the only option (i tried them all) that allowd me to start ubuntu was to reconfigure the display settings. so now it starts up fine but i seem to have lost compiz, oh no i hear you cry! not the pretty effects that make it all fun! well yes, and i'm afraid that was just the visible symptom of a far greater problem.

When trying to enable the desktop effects i discoverd the correct driver is no longer installed, ok so then i got to the hardware drivers panel...

The list of drivers is loaded with no problem, i can select the correct and recomended driver and when i click the activate button it downloads and installs the driver. but the green lights not comming on. and when i restart the system i have to go through the whole process again.

I am painfully aware that anyone who can help will need more information and some specifics no doubt, show me what to type into my terminal, and i will. i may be wrong but i hope this is helpfull.

root@ubuntu:~# glxinfo
name of display: :0.0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual or fbconfig

Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
3 GLXFBConfigs:
   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
Segmentation fault


root@ubuntu:~# glxinfo | grep direct
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual or fbconfig
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".


root@ubuntu:~# glxinfo | grep vendor
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual or fbconfig
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".


root@ubuntu:~# lspci | grep VGA
03:00.0 VGA compatible controller: nVidia Corporation G72M [Quadro NVS 110M/GeForce Go 7300] (rev a1) 


root@ubuntu:~# glxgears
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't get an RGB, Double-buffered visual


root@ubuntu:~# xrandr
Screen 0: minimum 640 x 480, current 1440 x 900, maximum 1440 x 900
default connected 1440x900+0+0 0mm x 0mm
   1440x900       60.0* 
   1360x768       60.0  
   1152x864       60.0  
   1024x768       60.0  
   800x600        60.0     56.0  
   640x480        60.0  


root@ubuntu:~# cat /etc/issue
Ubuntu 9.04 \n \l


root@ubuntu:~# uname -a
Linux ubuntu 2.6.29-02062904-generic #02062904 SMP Sat May 23 23:35:48 UTC 2009 x86_64 GNU/Linux

I hope some one can tell me im a dumb *** and i need to click there :D

Super Kim (not that super right now)

---

### Post by renkinjutsu on 2009-06-17
have you tried downloading and installing the nvidia drivers from here?
[http://www.nvidia.com/object/unix.html]("http://www.nvidia.com/object/unix.html")

*TO INSTALL THIS DRIVER, YOU MAY HAVE TO UNINSTALL/DEACTIVATE THE NVIDIA DRIVER PACKAGES ALREADY INSTALLED THROUGH JOCKEY-GTK*

to install this driver, you'll have to install kernel headers for your kernel.. do this with ```
sudo apt-get install kernel-headers-$(uname -r)
```

when you've downloaded the file, login to a virtual terminal (ctrl+alt+F1) stop GDM with: ```
sudo /etc/init.d/gdm stop
``` then browse to the downloaded file and install: ```
sudo sh *nvidiadriverhere.run*
```

when it asks to look for any preconfigured kernel from their ftp site, select no. Follow the instructions. At the very end of the installation, let nvida configure your xorg.conf

---

### Post by super kim on 2009-06-17
ok

$ sudo apt-get install kernel-headers-$(uname -r)
[sudo] password for user: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package kernel-headers-2.6.29-02062904-generic


what does that mean?

---

### Post by super kim on 2009-06-17
hi i have a problem getting my nvida drivers to activate.

it all started when i updated the kernel, to stop the system freezing.

you know the old song, there was an old woman who swallowed a spider...?


i posted on this subject earlier but i think i got the wron section sorry, heres the link to it anyway:
[http://ubuntuforums.org/showthread.php?t=1189732](http://ubuntuforums.org/showthread.php?t=1189732)

oh pleeease help me someone :(

---

### Post by super kim on 2009-06-17
> **renkinjutsu said:**
> have you tried downloading and installing the nvidia drivers from here?
[http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)

*TO INSTALL THIS DRIVER, YOU MAY HAVE TO UNINSTALL/DEACTIVATE THE NVIDIA DRIVER PACKAGES ALREADY INSTALLED THROUGH JOCKEY-GTK*

to install this driver, you'll have to install kernel headers for your kernel.. do this with ```
sudo apt-get install kernel-headers-$(uname -r)
```when you've downloaded the file, login to a virtual terminal (ctrl+alt+F1) stop GDM with: ```
sudo /etc/init.d/gdm stop
``` then browse to the downloaded file and install: ```
sudo sh *nvidiadriverhere.run*
```when it asks to look for any preconfigured kernel from their ftp site, select no. Follow the instructions. At the very end of the installation, let nvida configure your xorg.conf


i tried this but fell short at the first hurdle. what have i done wrong?

---

### Post by super kim on 2009-06-17
Ok, i've been trying this and that, and its got worse i think. now i'm not even getting the drivers listed in the harware drivers console. 

i seem to have 'a' driver but now i need the nvida driver. i feel i'm making progress in some ways, at least i'm learning

$ glxinfo | grep direct
direct rendering: Yes
$ glxinfo | grep vendor
server glx vendor string: SGI
client glx vendor string: SGI
OpenGL vendor string: Mesa Project

does anyone have any suggestions as to where i should go from here?

---

### Post by madnessjack on 2009-06-17
If I were you I would remove all the drivers and try again
```
sudo apt-get remove nvidia*
```I would recommend EnvyNG to make sure you're installing the right drivers
[http://albertomilone.com/envyngfaq.html#A](http://albertomilone.com/envyngfaq.html#A)

And if you ever get stuck at console when you reboot (because the drivers fail or whatever), this is your escape clause
```
sudo dpkg-reconfigure xserver-xorg
```Hope this helps :)

---

### Post by super kim on 2009-06-17
i was just going to ask how do i know which driver to download?
[http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)
from that list. does EnvyNG automaticly detect the correct one?
i am reading up on it now! 
thanks for your reply :)

---

### Post by super kim on 2009-06-17
@ubuntu:~$ sudo apt-get remove nvidia*
[sudo] password for ********: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting nvidia-96-kernel-source for regex ‘nvidia*’
Note, selecting nvidia-177-kernel-source for regex ‘nvidia*’
Note, selecting nvidia-glx-new-envy for regex ‘nvidia*’
Note, selecting nvidia-kernel-common for regex ‘nvidia*’
Note, selecting nvidia-common for regex ‘nvidia*’
Note, selecting nvidia-cg-toolkit for regex ‘nvidia*’
Note, selecting nvidia-glx-dev-legacy for regex ‘nvidia*’
Note, selecting nvidia-180-libvdpau for regex ‘nvidia*’
Note, selecting nvidia-glx-96-dev for regex ‘nvidia*’
Note, selecting nvidia-glx-dev-new for regex ‘nvidia*’
Note, selecting nvidia-glx-dev for regex ‘nvidia*’
Note, selecting nvidia-new-kernel-source for regex ‘nvidia*’
Note, selecting nvidia-71-kernel-source for regex ‘nvidia*’
Note, selecting nvidia-glx-ia32 for regex ‘nvidia*’
Note, selecting nvidia-glx-new for regex ‘nvidia*’
Note, selecting nvidia-glx-173-dev for regex ‘nvidia*’
Note, selecting nvidia-glx-dev-new-envy for regex ‘nvidia*’
Note, selecting nvidia-glx-src for regex ‘nvidia*’
Note, selecting nvidia-glx-lrm-dev for regex ‘nvidia*’
Note, selecting nvidia-kernel-source for regex ‘nvidia*’
Note, selecting nvidia-glx-envy for regex ‘nvidia*’
Note, selecting nvidia-173-kernel-source for regex ‘nvidia*’
Note, selecting nvidia-glx-173 for regex ‘nvidia*’
Note, selecting nvidia-glx-180 for regex ‘nvidia*’
Note, selecting nvidia-glx-177 for regex ‘nvidia*’
Note, selecting nvidia-glx-177-dev for regex ‘nvidia*’
Note, selecting nvidia-180-libvdpau-dev for regex ‘nvidia*’
Note, selecting nvidia-180-modaliases for regex ‘nvidia*’
Note, selecting nvidia-glx-legacy for regex ‘nvidia*’
Note, selecting nvidia-glx-dev-legacy-envy for regex ‘nvidia*’
Note, selecting nvidia-96-modaliases for regex ‘nvidia*’
Note, selecting nvidia-glx-71-dev for regex ‘nvidia*’
Note, selecting nvidia-180-kernel-source for regex ‘nvidia*’
Note, selecting nvidia-glx-legacy-envy for regex ‘nvidia*’
Note, selecting nvidia-kernel-src for regex ‘nvidia*’
Note, selecting nvidia-kernel-source-envy for regex ‘nvidia*’
Note, selecting nvidia-71-modaliases for regex ‘nvidia*’
Note, selecting nvidia-legacy-kernel-source for regex ‘nvidia*’
Note, selecting nvidia-glx-dev-envy for regex ‘nvidia*’
Note, selecting nvidia-legacy-kernel-source-envy for regex ‘nvidia*’
Note, selecting nvidia-new-kernel-source-envy for regex ‘nvidia*’
Note, selecting nvidia-glx-71 for regex ‘nvidia*’
Note, selecting nvidia-glx-96 for regex ‘nvidia*’
Note, selecting nvidia-173-modaliases for regex ‘nvidia*’
Note, selecting nvidia-glx for regex ‘nvidia*’
Note, selecting nvidia-glx-180-dev for regex ‘nvidia*’
Note, selecting nvidia-settings for regex ‘nvidia*’
E: Couldn't find package nvidia*

is this supposed to look like this? i'm thinking thats an e for error on the last line?

---

### Post by madnessjack on 2009-06-17
That just means there isn't any nvidia modules there, so you don't need to remove them.

EnvyNG does indeed figure out you're graphics and the driver you'll need, and then download, install and configure the rest for you.

It looks like a god send :D

---

### Post by super kim on 2009-06-17
wow this is looking good guys and gals!!
just one more lil question...

gtk, core, or qt?

these are the three different EnvyNG listings in my synaptic package manager.

---

### Post by super kim on 2009-06-17
.

---

### Post by madnessjack on 2009-06-17
[COLOR=White][COLOR=Black]EDIT: nevermind! :P[/COLOR]

I think I used gtk (if you're using GNOME) else, stick to qt. I'm not sure, but I think qt is cross platform.[/COLOR]

---

### Post by super kim on 2009-06-17
ok i want the qt, the core is a textual interface and the gtk is something else i think.
here i go ill let you know if i get this all sorted. fingers crossed

---

### Post by super kim on 2009-06-17
sorry i see the edity feature now, anyway my question regarding which option to install was, i see now a bit futile since when you select the qt option it ticks both anyway lol.

anyway its installed EnvyNG now so soon it will all be good :)

---

### Post by super kim on 2009-06-17
> **madnessjack said:**
> That just means there isn't any nvidia modules there, so you don't need to remove them.

EnvyNG does indeed figure out you're graphics and the driver you'll need, and then download, install and configure the rest for you.

It looks like a god send :D

EnvyNG detects the headers are missing from my kernel, and wont install the driver.

Ok new question, what are headers from my kernel and what have i done with them?

---

### Post by overdrank on 2009-06-17
Please do not create multiple threads on the same issue. I can cause confusion. Threads merged and closed new thread located [here]("http://ubuntuforums.org/showthread.php?p=7472533#post7472533").

---

