---
title: "d845glad video problems"
date: 2009-05-08
forum: New to Ubuntu
---

### Post by bolter40k on 2009-05-08
Hi, i am new to ubuntu.  I just installed 9.04.  I am running an old intel pentium 4 1.7 ghz a d645glad motherboard and i have an envision 710e monitor.  For some reason my resolution wont go above 800x400.  I've done some research and it appears i have to edit the xorg config file but i have no idea how or even what that is.  If anyone can help id greatly appreciate it.

---

### Post by Didius Falco on 2009-05-08
> **bolter40k said:**
> Hi, i am new to ubuntu.  I am running an old intel pentium 4 1.7 ghz a d645glad motherboard and i have an envision 710e monitor.  For some reason my resolution wont go above 800x400.  I've done some research and it appears i have to edit the xorg config file but i have no idea how or even what that is.  If anyone can help id greatly appreciate it.

Open a Terminal shell.

First, make a backup of it:

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.org
```To edit the xorg.conf file, type ```
gksudo gedit /etc/X11/xorg.conf
```xorg.conf is a file that store setting to do with your video card and display.

Do you know what you are going to add or change in xorg.conf?

---

### Post by bolter40k on 2009-05-08
when i enter the command for the backup i get this

cp: cannot create regular file `etc/X11/xorg.conf.org': No such file or directory

unfortunately i do not know what ims upposed to enter to get my display working properly where can i find this information


ok nevermind i made the backup i entered the command wrong, so now what do i do

---

### Post by Didius Falco on 2009-05-08
I left off the leading "/" on the second part of that command - sorry about that typo.

I just fixed it....

---

### Post by bolter40k on 2009-05-08
no problem im just happy someone can help um... what do i type in heres what is in the file

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"vesa"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

---

### Post by Didius Falco on 2009-05-08
Okay, before you start doing anything in xorg.conf, let's find out what resolutions are supported by your video card...do you know what card you have, btw?

Type this command in a terminal shell ```
xrandr
``` and post the output here.

---

### Post by bolter40k on 2009-05-08
Screen 0: minimum 640 x 480, current 1280 x 1024, maximum 1280 x 1024
default connected 1280x1024+0+0 0mm x 0mm
   1280x1024       0.0* 
   1024x768        0.0  
   800x600         0.0  
   640x480         0.0 

i dont have a card i all i have is the onboard chip

---

### Post by Didius Falco on 2009-05-08
> **bolter40k said:**
> Screen 0: minimum 640 x 480, current 1280 x 1024, maximum 1280 x 1024
default connected 1280x1024+0+0 0mm x 0mm
   1280x1024       0.0* 
   1024x768        0.0  
   800x600         0.0  
   640x480         0.0 

i dont have a card i all i have is the onboard chip

According to that output, you are currently running at 1280x1024 but at 0.0 FPS....

Okay, I'm going to have you try and set a mode from the command line.

Try 
```
xrandr --output VGA-0 --mode 1024x768
```

---

### Post by Didius Falco on 2009-05-08
Bolter40k,

Sorry, mate, but it's almost 7:30 pm here and I'm starving!!

Here are a couple of links you can study about xrandr and editing the xorg.conf file. You have a backup of it now, too, so you can always boot into your Live CD and restore the backup over your new xorg.conf file.

Otherwise, just wait until someone else jumps in to help you.


[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

[http://www.x.org/archive/X11R6.8.0/doc/xorg.conf.5.html](http://www.x.org/archive/X11R6.8.0/doc/xorg.conf.5.html)

[http://www.ubuntugeek.com/how-to-adjust-screen-resolution-on-ubuntu.html](http://www.ubuntugeek.com/how-to-adjust-screen-resolution-on-ubuntu.html)

Good luck!!

Regards,

Didius

---

### Post by bolter40k on 2009-05-08
thanks ill read up on these hopefully i can figure it out but the real problem will be my monitor specs.  thanks for the help and sorry about you waiting for a reply i fell asleep at my computer because it was 5 am where i live

---

### Post by bolter40k on 2009-05-08
unfortunately i guess im going back to windows.  I cant understand the terminal commands and what exactly i have to do... thanks for the help...   uhhhh windows :(

---

### Post by bolter40k on 2009-05-11
i know that the thread is old but unfortunately i am still having this problem and would greatly appreciate some help.  I really dont want to have to go back to windows just because i am not familiar enough with ubuntu.

now i do not know if this has to do with my problem but when i go to 
system-administartion-hardware drivers there are no proprietary drivers in use 

i have a intel pentium 4 1.7 ghz, intel d845glad with onboard video, and an envision 710e monitor 

please if anyone can help i would be so greatful because im just so fed up with windows and i really dont want to let a minor problem stop me from using linux

---

### Post by bolter40k on 2009-05-11
heres what is in my xorg config file 

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"vesa"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

---

### Post by bolter40k on 2009-05-11
plz the one thing i learned from ubuntu was its aim. a truly community driven user base with people helping others

plz carry this on as i will as i learn linux and help others with the things i can learn

---

### Post by bolter40k on 2009-05-11
if anyone has the time to help me out id greatly appreciate it however i am very busy with work and such so if anyone views this thread when i am not on plz send me an aim 

my aim is bolter40k im always on

my email is [email]bolter40k@sbcglobal.net[/email]

thank you for the help

---

