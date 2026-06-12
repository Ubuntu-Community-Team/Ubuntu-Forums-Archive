---
title: "ATI DRIVER INSTALL edit xorg.config"
date: 2009-02-10
forum: New to Ubuntu
---

### Post by garrydog on 2009-02-10
Hi
I have just installed /home/david/Desktop/ati-driver-installer-9-1-x86.x86_64.run .If I restart my computer to finish the install,I will get a black screen,and I will have to restart in recovery mode to get my desktop back and my xorg will be using the vesa driver ,my xorg is below .Can someone tell me how to edit this to change the screen resolution so that it will be in range of my monitors optimum resolution of 1280x1024,when I restart my computer .
Not sure that this will work,but not much else that I know to try .
Thanks .







Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	Monitor    "aticonfig-Monitor[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

---

### Post by jbrown96 on 2009-02-10
you might want to try running ```
aticonfig --intial
``` When the grub menu shows, choose the most recent kernel's recovery mode. Once it boots, choose the root shell and try running the command above. It should be able to auto-detect the optimal resolution and get everything set. Then you can test it by running ```
su - USERNAME
``` but change it to your user. Now you will be running commands as your user, which is good because you should never run X as root. Now run ```
startx
``` to start the x-server. If everything works, you are all set. Crtl+c will either take you back to the command line or restart. If you get to the command line, do ```
exit
``` to be root again, then ```
reboot
```

---

### Post by garrydog on 2009-02-10
> **jbrown96 said:**
> you might want to try running ```
aticonfig --intial
``` When the grub menu shows, choose the most recent kernel's recovery mode. Once it boots, choose the root shell and try running the command above. It should be able to auto-detect the optimal resolution and get everything set. Then you can test it by running ```
su - USERNAME
``` but change it to your user. Now you will be running commands as your user, which is good because you should never run X as root. Now run ```
startx
``` to start the x-server. If everything works, you are all set. Crtl+c will either take you back to the command line or restart. If you get to the command line, do ```
exit
``` to be root again, then ```
reboot
```
Hi  jbrown96
Thanks for your reply ,sorry but one thing I don't undrstand .
I know how to boot in recovery ,but I don't undrestand"choose the root shell ".
Will you please explain that for me .
Thank you .

---

### Post by jbrown96 on 2009-02-10
When you choose recovery mode, it used to be that you would just be dropped to a root shell. You would be at a command prompt that says something like ```
root@home:~$
```. you're all set to run the commands that I posted earlier. Newer versions of Ubuntu have some helpful options. There will be a grey box with several options and a red bar that can be used to make selections. There are options such as: reboot, dpkg, fix X server, root shell, and may be a couple extras. If you get this menu, choose the root shell then do the commands.

---

### Post by garrydog on 2009-02-10
After the command aticonfig --initial I got this return ,
found fglrx primary decice section
using/etc/x11/xorg.config
saved back-up to /etc/X11xorg.config.fglrx

Then I put in the rest of the commands,it rebooted to a black screen .I then booted in recovery ,try to fix xserver to get the desktop back .

---

### Post by zika on 2009-02-11
**@garrydog:**a new thread and the old problem. I thought that we've covered nearly everything in one of those threads ... ;) 
[http://ubuntuforums.org/showthread.php?t=1061790](http://ubuntuforums.org/showthread.php?t=1061790)
  [http://ubuntuforums.org/showthread.php?t=1056070](http://ubuntuforums.org/showthread.php?t=1056070)  
[http://ubuntuforums.org]("http://ubuntuforums.org/showthread.php?t=1063670")[/showthread.php?t=1063670]("http://ubuntuforums.org/showthread.php?t=1063670")  
[http://ubuntuforums.org/showthread.php?t=1055207](http://ubuntuforums.org/showthread.php?t=1055207)

again, that is the common piece of all these aforementioned threads (started by You) and this one, You do not say, after *startx* command, did You get a working GUI. that is the essential peace of information. without that kind of detail not a single person here could help You, because You are the only one in front of Your monitor and our help is relying on that. we are trying to be as precise as we can but You either do not supply the answer to our questions or go ahead to the next step even though the current step was not a success. I really want to help You but, please, cooperate.

---

### Post by garrydog on 2009-02-11
Hi Zika
I am trying my best to cooperate ,after putting the command " aticonfig --initial" in at the root prompt the return was,

found fglrx primary decice section
using/etc/x11/xorg.config
saved back-up to /etc/X11xorg.config.fglrx.

Then I put the "startx" command in ,and got the black screen again .I then rebooted and got the black screen agian,Had to do recovery then try to fix xserver to get the desktop back .Is this reply OK this is exactly what has happend .

---

### Post by zika on 2009-02-11
> **garrydog said:**
> Then I put the "startx" command in ,and got the black screen again.
this is the information that is important. every detail counts.

---

