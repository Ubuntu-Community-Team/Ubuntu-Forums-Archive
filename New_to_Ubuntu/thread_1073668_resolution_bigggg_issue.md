---
title: "resolution bigggg issue"
date: 2009-02-18
forum: New to Ubuntu
---

### Post by rcfllyer on 2009-02-18
Ok well windows is pretty much dead on my comp and until then I have to use ubuntu. Problem is (reason i never really used it before) is the res is wayyy too small. it is 800 by 600. THere is a black border around this now and its annoying me. I installed with wubi. Im tired of looking around forums and all i find is things like "did you install your card" "try changing refresh rate" I want some answers. Does anyone know how to change the .xorg file and how to make it work!?  im not a programmer so please help step by step how to do this.

---

### Post by pawnrocket on 2009-02-18
These are pretty good step by step instructions. 

[http://www.cyberciti.biz/faq/ubuntu-linux-how-to-reconfigure-x-windows-system-xorg-server/]("http://www.cyberciti.biz/faq/ubuntu-linux-how-to-reconfigure-x-windows-system-xorg-server/")

---

### Post by rcfllyer on 2009-02-18
oh and to add on to this. I cant get any updates working this is the error message i get.

i dont understand anything


E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

---

### Post by Kellemora on 2009-02-18
Hi RCF

If windows is DEAD, then Ubuntu running in Wubi shouldn't be working either.

You might try a fresh install putting Ubuntu in it's own partition, leaving the first partition for a reinstall of the Doze.

TTUL
Gary

---

### Post by kestrel1 on 2009-02-18
> **pawnrocket said:**
> These are pretty good step by step instructions. 

[http://www.cyberciti.biz/faq/ubuntu-linux-how-to-reconfigure-x-windows-system-xorg-server/]("http://www.cyberciti.biz/faq/ubuntu-linux-how-to-reconfigure-x-windows-system-xorg-server/")
Not the way I would do it personally.
I would do the following:```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.old
```
followed by ```
sudo gedit /etc/X11/xorg.conf
```
Replace what you see or select different parts of the following & paste in to the gedit file:
> # Fallback X.org config file
# FIXME: include the wacom devices (would only add noise at the current
#        development stage)

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
  screen 0 "screen1" 0 0
EndSection
Section "Module"
	Load		"glx"
	Load		"v4l"
EndSection
Section "device" #  
	Identifier	"device1"
	Boardname	"NVIDIA GeForce4 (generic)"
	Busid		"PCI:1:0:0"
	Driver		"nvidia"
	Screen	0
	Vendorname	"NVIDIA"
	Option		"NoLogo"	"True"
EndSection
Section "screen" #  
	Identifier	"screen1"
	Device		"device1"
	Defaultdepth	24
	Monitor		"monitor1"
	SubSection "Display"
		Depth	24
		Virtual 1280 1024	Modes		"1280x1024@60"	"1280x960@75"	"1280x960@60"	"1400x1050@60"	"1280x1024@75"	"1600x1200@65"	"1152x864@75"	"1600x1200@60"	"1024x768@60"	"1024x768@70"	"1024x768@75"	"832x624@75"	"800x600@60"	"800x600@75"	"800x600@72"	"800x600@56"	"640x480@75"	"640x480@72"	"640x480@60"
	EndSubSection
	Option		"AddARGBGLXVisuals"	"True"
EndSection
Section "monitor" #  
	Identifier	"monitor1"
	Vendorname	"Acer"
	Modelname	"Acer X193W"
	Horizsync	30.0-81.0
	Vertrefresh	55.0-76.0
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "640x480@72" 31.5 640 664 704 832 480 489 491 520 -vsync -hsync
  modeline  "640x480@75" 31.5 640 656 720 840 480 481 484 500 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "832x624@75" 57.284 832 864 928 1152 624 625 628 667 -vsync -hsync
  modeline  "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
  modeline  "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -vsync -hsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
  modeline  "1280x1024@75" 135.0 1280 1296 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@75" 129.86 1280 1368 1504 1728 960 961 964 1002 -hsync +vsync
  modeline  "1400x1050@60" 122.61 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
  modeline  "1600x1200@65" 175.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1600x1200@60" 162.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
	Gamma	1.0
EndSection
Section "ServerFlags"
EndSection
I expect some will disagree, but it works for me.

---

### Post by rcfllyer on 2009-02-18
i can access all my files from ubuntu which is nice. i got the missing dll back but I have another error message. Session5_Initialization_Failed so idk what to do there.

---

### Post by kestrel1 on 2009-02-18
> **rcfllyer said:**
> oh and to add on to this. I cant get any updates working this is the error message i get.

i dont understand anything


E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
Try this from the terminal```
sudo dpkg --configure -a
```

---

### Post by rcfllyer on 2009-02-18
wait i just take everything i see out and then copy that code into it?

the code beign the long one you gave me

---

### Post by kestrel1 on 2009-02-18
> **rcfllyer said:**
> wait i just take everything i see out and then copy that code into it?

the code beign the long one you gave me
Yes, as long as you have backed up the original with the cp command first. Should work. You will need to reboot or restart X server
You should then be able to resize your screen.

---

### Post by rcfllyer on 2009-02-18
backup? ok please restate the steps exactly.in an easy to understand way.

---

### Post by kestrel1 on 2009-02-18
Open a terminal Window & copy this command:```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.old
```
That gives you a backup of your original xorg.conf file before editing it with```
sudo gedit /etc/X11/xorg.conf
```

---

### Post by semitone36 on 2009-02-18
It doesnt really sound like you WANT linux on your system.  If I were you, assuming that your windows partition is corrupted, I would just reinstall windows.  

Wubi is meant to be run on a properly functioning windows operating system.  Since windows isnt working for you, that explains why you are having issues with ubuntu.  Unless you do a fresh install of either Windows or Ubuntu, youre just trying to save a sinking ship.

---

### Post by rcfllyer on 2009-02-18
it always did this for me even when windows was running good. I want to use ubuntu at least long enough to back up my data. WHICH MAY NOT BE POSSIBLE. yeah i copied and pasted all the code and guess what happenes. I restart the computer AND IT RUNS IN SOME WEIRD LOW GRAPHICS MODE. pretty much a black screen where i can hear but I cant do anything!

---

### Post by rcfllyer on 2009-02-18
oh you can choose reconfigure graphics or troubleshoot error

---

### Post by rcfllyer on 2009-02-18
oh and to your sig. I have used sudo before becsaue places liek this tell me to.

---

### Post by semitone36 on 2009-02-18
lol my sig says dont use "sudo rm -rf" (all one command)

If you were to use it you would basically be telling your computer "I order you to destroy yourself"

"sudo" on its own is okay so long as you understand what the commands that follow it do.

Anyways Im sorry to hear about your files.  Has your resolution situation improved at all?  If not I can give you the commands to restore it to what it was before you copy/pasted all that code.

---

### Post by jrandolph on 2009-02-18
> **rcfllyer said:**
> oh and to your sig. I have used sudo before becsaue places liek this tell me to.

his signature tells u not to use sudo rm -rf or rm -rf because he is trying to help people from asses that give unknowing users malicious commands like the ones in his sig that will do very very bad things

---

### Post by rcfllyer on 2009-02-18
well i chose reconfigure to defauly
didnt work. So I started it up in recovery mode and I will bakcup all my windows data (word doc. pictures files ect.) and then I think I will start fresh. and maby install ubuntu also. when going through something like this it kinda makes me want to have it :D

---

### Post by semitone36 on 2009-02-18
Really?  Then perhaps you will do well in the Linux community.  Its not often that I meet another person who actually enjoys troubleshooting a comp.

I wish you luck in your experience!

---

### Post by rcfllyer on 2009-02-18
well I got ubuntu running again and here is what I plan on doing.

backup all my windows data (dad will give me one of his external hardrives)
get rid of ubuntu and windows (help from online)
reinstall windows AND ubuntu separate partitions and I will try to get the res good if it is still messed up. 

its fun only becasue i have 2 other computers i can use for doing real work on :D if this was my only computer i would be annoyed becasue i cant go on the internet to get help from you. of course rightnow im on ubuntu but in that weird thing with low graphics mode its a good thing i had another computer.


hey by any chance do you know how to get rid of an OS and then install windows 2000 and Ubuntu on separate partitions? windows 2000 I have the cd ubuntu I belive you have to make. 


ps. ugg i dont like low res. but im not taking any chances anymore until i can get my files on that external hd.

---

### Post by kestrel1 on 2009-02-18
I wasn't thinking earlier. Very sorry, the xorg.conf file was for older Nvidia graphics cards.
I should have asked what graphics card you have & to give us the results of[codelspci[/code]
I apologize again for my mess up.
I think a re-install is a very good idea & separate partitions for Windows & Ubuntu even better.
If you want to install Win2K, you can do so by booting from the Win2K CD & going through the process. Select the whole drive or create a partition for it, Format the partition & continue to install Windows. Then use the Ubuntu CD & resize the drive or create a partition on the unused space. Continue to install Ubuntu & reboot your machine when prompted, you should have Grub load up with options for Win2K & Ubuntu.

---

### Post by semitone36 on 2009-02-18
Windows ME???? Please tell me you have a copy of xp or at the very least vista around...

Well regardless of what windows OS you choose, you just need to set your boot menu in BIOS to boot from your cd drive first.  Then put the windows cd in the drive before you boot your computer and you should be able to do a fresh install over your entire hdd.

After that download the ubuntu .iso from [www.ubuntu.com](www.ubuntu.com) and burn it to a disk and repeat the process above.

Just be sure to:
1. Install Ubuntu AFTER windows
and
2. When installing ubuntu, install it as its own partition, not as a fresh install

---

### Post by rcfllyer on 2009-02-18
windows 2000 is all that works on this comp. Its old ya know. i have xp on my other comp. Im thinking it may be smarter to install ubuntu maby with wubi. That way I can back up my data like im going to do now :D when they run together I can acces my windows files from here even if windows doesnt work. 



its ok that it didnt work. I got it back to normal anyways.

---

### Post by kestrel1 on 2009-02-18
I wouldn't use Wubi. You can still access your Windows files with Ubuntu installed on a separate partition.

---

### Post by rcfllyer on 2009-02-18
oh you can? I didnt know that. cool.

---

### Post by kestrel1 on 2009-02-18
Yes Linux is very cool. It can read & write to FAT32 & NTFS formatted drives, so the version of Windows is not important.

---

### Post by rcfllyer on 2009-02-18
I wont be able to do anything as of now until I get the hardrive and cds from my father and then I will save everything (maybe and hour or so of saving) and then I will install windows 2000 from his cd. i have never installed an os before but with online help ithink i can do it.

---

### Post by kestrel1 on 2009-02-18
To be honest there are a lot of people that are frightened of installing an OS, but to to be perfectly truthful it is easy. If you aren't affraid of loosing your data or like you are backing it up, it really does most of it for you. With a little knowledge, you shouldn't go wrong.
If you get in to difficulties contact me via my website [http://www.kcsdorset.co.uk](http://www.kcsdorset.co.uk) or here.

---

### Post by rcfllyer on 2009-02-18
well he didnt give me OS cds instead a recovery cd. Will I be able to do the partitioning and stuff with it? It should delte ubuntu also right? RIght now im backing up my data.

---

### Post by kestrel1 on 2009-02-18
If it is a Windows "K recovery CD I expect you will be OK, although if this is not the CD for your system you are breaking the copyright law unless you have your own registration key.
Most Win2K recovery media is infact just a normal install CD, but may have a few extra bits of software from the manufacturer on the CD.

---

### Post by rcfllyer on 2009-02-18
its for the system. has the model number and everything. My dad pretty much gave it to me and said "press enter". so yeah i have all my stuff backed up and I will be doing a system recovery.

---

### Post by rcfllyer on 2009-02-18
also. which would you reccomend? I dont want to keep using Ubuntu as the res issue will probably happen again. I was thinking mint looks good? what do you think about mint?

---

### Post by magh-87 on 2009-02-18
> **semitone36 said:**
> lol my sig says dont use "sudo rm -rf" (all one command)

If you were to use it you would basically be telling your computer "I order you to destroy yourself"

"sudo" on its own is okay so long as you understand what the commands that follow it do.

Anyways Im sorry to hear about your files.  Has your resolution situation improved at all?  If not I can give you the commands to restore it to what it was before you copy/pasted all that code.

In the hopes to create a better resolution on this, I edited that file and am now stuck with 800x600 screen resolution. I've tried reverting back to the file I had before but it doesn't work. The strange thing is that when I rebooted the computer the first time it asked me about my monitor specs and actually seemed to be working fine with that so I'm not sure what happened to that... any thoughts?

---

### Post by kestrel1 on 2009-02-19
> **rcfllyer said:**
> also. which would you reccomend? I dont want to keep using Ubuntu as the res issue will probably happen again. I was thinking mint looks good? what do you think about mint?
Yes Linux Mint is very good, but you have to remember that Mint is Ubuntu Based, so you may have the same problems again.
I am sure that this could be sorted out, but you may need a bit of patience. No good flying off the handle & throwing the machine out of the window when it doesn't work first time :lolflag:
There are many Linux Distro's, but mostly everyone on this forum will try to steer you in the right direction. Ubuntu is probably the best community supported Linux Distro & most posters really want to help you out. So don't give up just yet. Even though we will try to help with other distro's as well.

---

### Post by rcfllyer on 2009-02-19
ok i have everything installed on windows. Im not sure I want to take a chance of messing up my computer by doing the whole linux thing. I may just keep wubi the way I had it. According to what i heard the first time wubi did partitions for you and when I had it it says it was under a different partition so idk.

---

### Post by kestrel1 on 2009-02-19
If you don't want to take a chance I guess you have two options open to you. You can go down the wubi route or you could install VirtualBox & install Ubuntu that way.
Virtual box is a very nice piece of software that enables you to have virtual machines installed on your system. It is also Free.
Find out about it here: [http://www.virtualbox.org/](http://www.virtualbox.org/)
It is just like any other software that you install, so there is no way to completely mess up your system.
I use it to try out other Linux Distro's & even Windows 7.

---

