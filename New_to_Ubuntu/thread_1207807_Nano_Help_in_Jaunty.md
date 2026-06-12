---
title: "Nano Help in Jaunty"
date: 2009-07-08
forum: New to Ubuntu
---

### Post by fly360 on 2009-07-08
How do I write this in Nano? 


3. sudo nano /etc/X11/xorg.conf
4. Add a line 'Option "UseInternalAGPGART" "no"' under 'Section "Device"' and save the file.
5. sudo reboot now

---

### Post by halitech on 2009-07-08
open a terminal and type in that code

use your arrow keys to get where you want to add info

press CTRL + O to save the file, CTRL + X to exit

do a normal reboot

---

### Post by fly360 on 2009-07-08
I have ATI installed and now it will not boot. I've tried the recovery console and the same thing happens. I got the above steps in a thread in Installations earlier, unfortunately no has answered that reply.

---

### Post by fly360 on 2009-07-08
From "add a line" on? I don't understand the Nano way yet.

---

### Post by finer recliner on 2009-07-08
nano is a text editor that works in the terminal (it doesnt have its own graphical window).

step 3 in your instructions does the following: open the file /etc/X11/xorg.conf with nano text editor with super-user priveledges (thats what "sudo" does)

you can move the cursor around in nano by using the keyboard's arroy keys. remember, your mouse wont work in the terminal.

after make the changes to your file, save it by pressing ctrl+o. then exit the editor (and return to the command line) by pressing ctrl+x.

hope this helps!

---

### Post by fly360 on 2009-07-08
What I'm asking is how do I write it.
Like This?
<option>
UseInternalAGPGART
no
<section>
Device
Then control "O"?

---

### Post by fly360 on 2009-07-08
Does anyone understand what I'm trying to ask or am I going back and reinstalling Ubuntu over a ATI driver issue? I understand the sudo commands but not the Nano. What is getting me is the "Options and Sections" part. I also understand the key functions like "CTRL X".

---

### Post by BryD on 2009-07-08
Use the keyboard !

---

### Post by .nedberg on 2009-07-08
In terminal
```
sudo nano /etc/X11/xorg.conf
```

Find a section with
```
Section "Device"
```

Add
```
Option "UseInternalAGPGART" "no"
```
in that section.

Press:
Ctrl+o to save
Ctrl+x to exit

```
sudo reboot
```
to reboot

---

### Post by .nedberg on 2009-07-08
Here is how my Device section looks:
```

Section "Device"
        Identifier      "Configured Video Device"
        Option "Twinview" "true"
        Option "MetaModes" "1280x1024,1280x1024;1280x1024,1024x768;1024x768,1024x768"
        Option "SecondMonitorHorizSync" "30-65"
        Option "SecondMonitorVertRefresh" "50-75"
        Option "ConnectedMonitor" "CRT, CRT"
        Option "TwinViewOrientation" "RightOf"
        Driver  "nvidia"
        Option  "NoLogo"        "True"
EndSection

```

It is an nvidia card, but you get the idea!

---

### Post by .nedberg on 2009-07-08
If you have no "Section "Device"", then make one, and remember to add the EndSection

---

### Post by halitech on 2009-07-08
here is mine with the ati drive install
```
daryl@debian:~$ cat /etc/X11/xorg.conf
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
	BusID       "PCI:1:5:0"
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

daryl@debian:~$ 


```

---

### Post by fly360 on 2009-07-08
Thanks for the help, when I get into nano none of the screen shots that was show is on mine. The screen is blank, that might be why I was having such a problem.

---

### Post by fly360 on 2009-07-08
I tried:
cat /etc/x11/xorg.conf
It replies no such file or directory 
???????

Nano also comes up blank

---

### Post by oldos2er on 2009-07-08
The proper name is /etc/X11/xorg.conf. Linux is case-sensitive.

---

### Post by sdlynx on 2009-07-08
> **fly360 said:**
> Does anyone understand what I'm trying to ask or am I going back and reinstalling Ubuntu over a ATI driver issue? I understand the sudo commands but not the Nano. What is getting me is the "Options and Sections" part. I also understand the key functions like "CTRL X".

All you have to do is write it exactly as it is said.  Use the quotes just like it says.

---

### Post by fly360 on 2009-07-08
I got into it nano, the line mod did not work. It still won't boot up, so I'm reinstalling the OS now. Thanks everyone for the time and inputs, I greatly appreciate it.

---

### Post by whitethorn on 2009-07-08
just in case you want to edit a file, and nano doesn't cut it for you.  Try using

gksu gedit /etc/X11/xorg.conf

---

