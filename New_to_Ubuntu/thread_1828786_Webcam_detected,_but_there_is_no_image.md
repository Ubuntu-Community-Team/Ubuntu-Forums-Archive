---
title: "Webcam detected, but there is no image"
date: 2011-08-19
forum: New to Ubuntu
---

### Post by hr_caldeira on 2011-08-19
I used to use my Samsung Galaxy 5 as a webcam, but now that I've installed ubuntu 11.04 I'm having some problems.
I install the droidcam app (that allows me to connect mobile and computer) and skype, cheese and vlc detect the device but instead of the image from the cam, it shows just a black screen.
GStreamer says: Video for Linux 2 (v4l2): Device '/dev/video0' cannot capture in the specified format

:confused:

Any suggestions?

---

### Post by no2498 on 2011-08-20
put the program name you use behind this
in a terminal

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so cheese

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so

---

### Post by Dragonbite on 2011-08-20
If that works, then you can edit the menu entries to include the **LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so** in the run command.  I've had to do that recently as well. It worked fine with the older Ubuntu, but not with the newer.

---

### Post by no2498 on 2011-08-20
did you use the bottom test in GStreamer 
it should show the cam
im on 10.04 and vlc kills my cam 
i need to try GStreamer 5 or 6 times to get it back running

---

### Post by hr_caldeira on 2011-08-20
[no2498]("http://ubuntuforums.org/member.php?u=906707")
I didn't get it. Put the program name behind? Could you give an example with a generic program name?
I ran the commands just like you wrote and it didn't work.
And I used the Gstreamer test bottom and it gave this (as said on original post): Video for Linux 2 (v4l2): Device '/dev/video0' cannot capture in the specified format

:confused:

thx

---

### Post by no2498 on 2011-08-21
this should open skype
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype

in a terminal type dmesg click enter
look close to the bottom did it find your cam

in the terminal type lsusb
should give a number and name of your cam
close the terminal
in your package manager find and install xawtv and guvcview
try the cam in them

---

### Post by hr_caldeira on 2011-08-21
> **no2498 said:**
> this should open skype
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype

in a terminal type dmesg click enter
look close to the bottom did it find your cam

in the terminal type lsusb
should give a number and name of your cam
close the terminal
in your package manager find and install xawtv and guvcview
try the cam in them

When I use the first command, terminal gives me this:

ERROR: ld.so: object '/usr/lib/libv4l/v4l1compat.so' from LD_PRELOAD cannot be preloaded: ignored.
/usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so: wrong ELF class: ELFCLASS64

(<unknown>:3507): Gtk-WARNING **: Failed to load type module: /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so

/usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so: wrong ELF class: ELFCLASS64

(<unknown>:3507): Gtk-WARNING **: Failed to load type module: /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so


(<unknown>:3507): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so: wrong ELF class: ELFCLASS64

(<unknown>:3507): Gtk-WARNING **: Loading IM context type 'ibus' failed

(<unknown>:3507): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so: wrong ELF class: ELFCLASS64

(<unknown>:3507): Gtk-WARNING **: Loading IM context type 'ibus' failed
/usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so: wrong ELF class: ELFCLASS64

(<unknown>:3507): Gtk-WARNING **: Failed to load type module: /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so

/usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so: wrong ELF class: ELFCLASS64

(<unknown>:3507): Gtk-WARNING **: Failed to load type module: /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so


(<unknown>:3507): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so: wrong ELF class: ELFCLASS64

(<unknown>:3507): Gtk-WARNING **: Loading IM context type 'ibus' failed

I installed the 2 programs you told and the cam runs fine on both but still i can't use it on skype nor msn.

thx

---

### Post by Cpierce on 2011-08-21
this fixed to web cam for me in skype

[http://ubuntuforums.org/showpost.php?p=8390933&postcount=13](http://ubuntuforums.org/showpost.php?p=8390933&postcount=13)

---

### Post by pbink on 2011-12-25
My issue is very similar, so I hope I'm not jacking here...

I'm using DroidCam on my Android Droid X phone to emulate a webcam in hopes of using it in Skype.  There is a DroidCam linux client, which needs to be run after the phone's DroidCam app is run, and then Skype sees the video device as DroidCam (/dev/video0) in the "Select webcam" drop-down, but the test video window stays just a black screen after clicking "Test".

I tried the launcher modifications mentioned above to no avail.  I used XawTV to test the camera and it works perfectly there.  Hope this sheds some insight.  Any ideas?

---

### Post by Anthony T on 2012-07-27
> **pbink said:**
> My issue is very similar, so I hope I'm not jacking here...

I'm using DroidCam on my Android Droid X phone to emulate a webcam in hopes of using it in Skype.  There is a DroidCam linux client, which needs to be run after the phone's DroidCam app is run, and then Skype sees the video device as DroidCam (/dev/video0) in the "Select webcam" drop-down, but the test video window stays just a black screen after clicking "Test".

I tried the launcher modifications mentioned above to no avail.  I used XawTV to test the camera and it works perfectly there.  Hope this sheds some insight.  Any ideas?

I am having the same problem. I know the solution, I just don't know how to do it. You need to download Droidcam 3.5.1. That is what i can't do because the instructions don't work. Here is the link to my problem with it in case someone here wants to help me out as well. [http://ubuntuforums.org/showthread.php?t=2033842&highlight=droidcam](http://ubuntuforums.org/showthread.php?t=2033842&highlight=droidcam)

---

### Post by NikTh on 2012-07-27
Hi , 
if you want specific for skype , try to install the newest version [[COLOR=Blue]Skype 4.0 for Linux[/COLOR]](http://www.skype.com/intl/en-us/get-skype/on-your-computer/linux/) 

Thanks

---

