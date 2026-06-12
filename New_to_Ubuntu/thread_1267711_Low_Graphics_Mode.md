---
title: "Low Graphics Mode"
date: 2009-09-16
forum: New to Ubuntu
---

### Post by Obso1337 on 2009-09-16
Hello everyone, and a pre-emptive thank you for all the help you guys give to newbs like me. 
Ok, so I used UNetbootin to turn my flash drive into a bootable Ubuntu 9.04 because I'm sick of having Windows on this old crappy Dell computer. That was easy enough, but I ran into a problem after booting from USB. After initial loading Ubuntu comes up with a message that it is in "low graphics mode" because my screen, drivers...ect could not be found.
I tried to choose the option "proceed in low graphics mode for this session" but then I could hear ubuntu intro music but see nothing.
Frankly I have no idea where to even begin to fix this.
This computer has an ancient Windows XP install right now that was ravaged by malware, spyware, viruses, you name it. (It was my mom's old one I'm trying to make usable again) so It's entirely possible there are drivers missing despite Windows saying everything is fine.

---

### Post by AlexenderReez on 2009-09-16
please do try install ubuntu-desktop


> sudo apt-get install ubuntu-desktop

---

### Post by Obso1337 on 2009-09-16
Um, the computer is currently running on Windows. I cannot see to do anything when I try to boot Ubuntu.

---

### Post by dzon65 on 2009-09-16
Have you considered wubi-install instead of usb?

---

### Post by Obso1337 on 2009-09-16
> **dzon65 said:**
> Have you considered wubi-install instead of usb?
I looked that up. Cool option, but I'm afraid it won't work in this case. The computer I am trying to put Ubuntu on is old and has virtually no memory. The 20GBs it has are full of old crap I can't get rid off because of how corrupt so many files on here are. It takes me several minutes just do something simple like post here because it is constantly stopping and giving "low memory condition" warnings, and I can't increase the paging file any more than I already have because there is no more room. 
I really need it to be a USB install. (LiveDisk is no-go. old Dell CD drives can't read ISO fast enough)
The bigger issue though is that even if I could install another way I imagine I would still have the same graphics problems.
If anyone has any ideas about how to isolate what the problem is I would really appreciate it.

---

### Post by tomBorgia on 2009-09-16
Hi,

I'd try and install xubuntu or something similar... sounds like your hardware is a bit too old for ubuntu (the gnome desktop manager is quite resource hungry... which it'll be trying to load from your usb disk when you boot up... probably just runs out of memory and hangs.)

Tom.

---

### Post by Obso1337 on 2009-09-16
I'll reformat the USB drive into Xubuntu and try again. I'll come back tomorrow and let you know how it worked out.
Thanks Tom.

---

### Post by Obso1337 on 2009-09-16
Earlier today I tried putting xubuntu on the Flash drive and met with the same result. Once it boots up I get a window that says 
"Ubuntu is running in low graphics mode. Your Screen, graphics card, and input device could not be detected correctly. You will need to configure these yourself".
Choosing either "run in low graphics mode for this session" or "create new configurations for this hardware" both meet with a black screen and nothing else.

---

### Post by Obso1337 on 2009-09-16
I just tried with DSLinux. I was actually able to run it, but it too had some kind of trouble with graphics that I didn't really understand. Below is a rough recreation of what came up after ubninit was loaded:
"You have passed an unknown mode.
Video Adapter: VESA VGA
MODE: COLSxROWS
Choose a mode below, press return to continue or wait 30 seconds"
then several options to choose using the F keys all in the format of:
"F3: 80x60"
then then a command line with the sentence "or 'scan'". At first I chose 
I chose to "scan" which ended just like Unbuntu, I couldn't see anything. 
I rebooted and chose continue the next time, which ended in DSL running fine. 
Clearly something is wrong with the graphics components of this computer, I just need help finding out what, as I have no clue how to go about it. 
This comp really isn't that old, it's from 2005. It should be able to run Ubuntu fine, as after a great deal of work it is doing so with Windows XP.

---

### Post by Obso1337 on 2009-09-18
One last bump before I give up and take this to another forum. 
Come on guys! :-(

---

### Post by checoimg on 2009-09-18
A suggestion from another noob. I don't know if this qould help but I hope it can. When you boot and get the low performance message press "CTRL+ALT+F1" to get where you can put commands and try the "sudo apt-get install ubuntu-desktop" option. I'm having the same problem and I'm on a new Laptop so maybe is not about old hardware.

Hope it helps.

---

### Post by Obso1337 on 2009-09-23
> **checoimg said:**
> A suggestion from another noob. I don't know if this qould help but I hope it can. When you boot and get the low performance message press "CTRL+ALT+F1" to get where you can put commands and try the "sudo apt-get install ubuntu-desktop" option. I'm having the same problem and I'm on a new Laptop so maybe is not about old hardware.

Hope it helps.

Thanks for trying to help, but this was not the issue. When done the above suggestion simply tries to update the desktop which is already the latest update. 
I'm pretty sure if someone could just tell me how to "configure" my video adapter and such I could get this to work, but as it stand this comp will not be fixed until someone does as much, which no one seems able or willing to do.

---

### Post by tomBorgia on 2009-09-25
> **Obso1337 said:**
> Thanks for trying to help, but this was not the issue. When done the above suggestion simply tries to update the desktop which is already the latest update. 
I'm pretty sure if someone could just tell me how to "configure" my video adapter and such I could get this to work, but as it stand this comp will not be fixed until someone does as much, which no one seems able or willing to do.

I'm sure plenty people on here know how to configure the xorg graphics bit manually... anyone who used Linux in the dark days will know it's not especially easy for a first timer!

You'll need to edit ```
/etc/X11/xorg.conf
```

To do this first backup the file - Log in to the command prompt and type 

```
cd /etc/X11
```

```
cp xorg.conf xorg.bak
```

Then edit the file -

```
sudo nano xorg.conf
```

This will load the file in "nano" text editor... add the following in "section Screen" -

```
SubSection "Display"
                Depth           16
                Modes           "800x600" "720x400" "640x480"
        EndSubSection
```

You may also need to edit the "section Device" bit to something looking like this (but for your graphics card)

```
Section "Device"
        Identifier      "ATI Technologies Inc ATI Default Card"
        Driver          "vesa"
        BusID           "PCI:1:5:0"
EndSection
```

type ctrl-x to exit the editor - save the file.

Type startx and see what happens... it'll give you some detailed output if it fails which you can either post here or google...

---

### Post by Obso1337 on 2009-09-27
First of all, Thank you very much Tom! :-D

I have a few questions, as I am a complete newb and have never tried something like this before. I appreciate your patience.
> **tomBorgia said:**
> 

You may also need to edit the "section Device" bit to something looking like this (but for your graphics card)

```
Section "Device"
        Identifier      "ATI Technologies Inc ATI Default Card"
        Driver          "vesa"
        BusID           "PCI:1:5:0"
EndSection
```
I'm unsure what I should use to make these match my graphics card. I looked in the device manager at the graphics card's info and all I see is under general:
Intel(R) 82845G/GL/GE/PE/GV Graphics Controller
Location: PCI bus 0, device 2, function 0
Under Driver:
Provider: Intel Corporation
Date 6/21/2005
Version: 6.14.10.4342
I gather for BusID I should use "PCI:0:2:0", but I am unsure what to put for the other two values for this particular graphics card, or how to find out. 

> **tomBorgia said:**
> 
type ctrl-x to exit the editor - save the file.
Just want to be crystal clear, because I will screw this up if given the smallest task to figure out for myself. By this sentence did you mean that Ctrl-x will exit and save, or will give me an option to save then exit, or I need to do something else to save the changes?

---

### Post by tomBorgia on 2009-09-28
> **Obso1337 said:**
> First of all, Thank you very much Tom! :-D

I have a few questions, as I am a complete newb and have never tried something like this before. I appreciate your patience.

I'm unsure what I should use to make these match my graphics card. I looked in the device manager at the graphics card's info and all I see is under general:
Intel(R) 82845G/GL/GE/PE/GV Graphics Controller
Location: PCI bus 0, device 2, function 0
Under Driver:
Provider: Intel Corporation
Date 6/21/2005
Version: 6.14.10.4342
I gather for BusID I should use "PCI:0:2:0", but I am unsure what to put for the other two values for this particular graphics card, or how to find out. 


Just want to be crystal clear, because I will screw this up if given the smallest task to figure out for myself. By this sentence did you mean that Ctrl-x will exit and save, or will give me an option to save then exit, or I need to do something else to save the changes?

Yep the PCI bit is correct... if you leave "vesa" it will use the generic driver which *should* be most compatible...

Yes sorry thats not clear! ctrl-X will then ask you if you want to save the file and then exit (at the bottom of the screen it'll ask for the filename to save under... so just press enter and it'll save it under the same name).

---

### Post by Obso1337 on 2009-09-28
What about for "Identifier"? Should I use "Intel(R) 82845G/GL/GE/PE/GV Graphics Controller"?

---

### Post by tomBorgia on 2009-09-28
```
Section "Device"
	Identifier	"Configured Video Device"
	
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

```GOOD job your double checking! It's monday AM and brains not firing on all cylinders... Your xorg.conf has to tie up as above... sot he section screen has to have the correct identifier for the monitor / device sections so if you change the identifier you need to change it further down in the screen section! You can just leave the Identifier as default really and just edit the PCI / Driver bit.

Bit of a major thing to miss out really... sorry about that!

---

### Post by Obso1337 on 2009-09-28
> **tomBorgia said:**
> 
Bit of a major thing to miss out really... sorry about that!

No problem. Thanks again for your help. I'll be giving this a go in a little bit, and will let you know how it went.

---

### Post by Obso1337 on 2009-09-30
It didn't work. When I tried to backup the file you mentioned I found it didn't even exist. I tried creating it but that didn't work either and it went crazy basically. I'm pretty sure the Flash Drive I used with UNetBootin was faulty. 
I was able to clean the crappy Windows install up though, and clear a lot of room on it. I'm going to recreate the bootable flash drive and try one last time, if it doesn't work though I'm going to give up and tell my mom she'll have to use this computer and it will be slow forever. : -/

Thanks a ton anyway though everyone for trying to help! :-D

---

### Post by tomBorgia on 2009-10-01
Yer didn't say it was easy =D

That file absolutely positively would be there... methinks you may have been trying to work relative to your home directory instead of the root of the file system... If you try again might be worth having a read up on unix / linux file systems - if you need to mess around with anything in command line you'll need some idea of where you are within the system!!!

Hopefully it was just the usb drive as you say... good luck!

---

### Post by pedro3005 on 2009-10-01
Try the alternate installation. Then you'll probably get to install ubuntu just fine, but without a desktop environment. Then you'd fix the xorg.conf issue and install one. Since you can't use the actual CD, might I suggest: [http://www.netboot.me/](http://www.netboot.me/)
Helped me when I had to install ubuntu using nothing but a floppy on an old laptop ;)

---

