---
title: "Youtube - Full Screen Slow/ low frame rate"
date: 2009-04-07
forum: New to Ubuntu
---

### Post by gr3yfox on 2009-04-07
hi, im currently running ubuntu 8.10 GNOME 64bit on my AMD64 4200+ with an Nvidia 7600gt using nvidia drivers 177.

i used this method( [http://news.softpedia.com/news/How-to-Install-Adobe-Flash-Player-64-bit-on-Ubuntu-8-10-98076.shtml](http://news.softpedia.com/news/How-to-Install-Adobe-Flash-Player-64-bit-on-Ubuntu-8-10-98076.shtml) ) to install my flash player.

it runs perfectly fine unless i full screen, i have decent internet connect for the videos load fairly fast and look normal in the small player, but once full screened it becomes very slow and choppy. my google video runs fine in full screen, just youtube runs slow fullscreen, maybe others too but not that i have seen yet. i have looked all over and have found different but non helpful ways to fix it. ie. different versions of linux and/or video cards.

any suggestions? =]

---

### Post by MockY on 2009-04-07
Disable the 177 drivers and install the 180 drivers instead found here
[http://us.download.nvidia.com/XFree86/Linux-x86_64/180.44/NVIDIA-Linux-x86_64-180.44-pkg2.run](http://us.download.nvidia.com/XFree86/Linux-x86_64/180.44/NVIDIA-Linux-x86_64-180.44-pkg2.run)
Not saying it will solve your issue, but it is by far a better driver.

---

### Post by gr3yfox on 2009-04-07
i deactivated the 177, but the download wont run, says "Could not open the file /home/gr3yfox/Desktop/NV&#8230;ux-x86_64-180.44-pkg2.run using the Unicode (UTF-8 ) character coding."

unless i have to install it a certain way, i just tried running the app.

---

### Post by MockY on 2009-04-07
You can't install the driver in Gnome. You have to exit out of it pressing Ctrl+Alt+F2, then type ```
sudo killall gdm
``` and then ```
sudo sh /.driverfile.run
```

---

### Post by gr3yfox on 2009-04-09
when i did the first command it went to some black screen.. well ill try that another time, anyone have suggestions for my current situation with my current driver (177)?

---

### Post by pbotros1234 on 2009-04-09
I would definitely update the driver instead of messing with the 177 driver.

Once you press Ctrl+Alt+F2, you will be dumped to a linux console, a black screen that will prompt you to log in with username and password. Once you've logged in with the correct credentials, run the two other commands from the previous post.

---

### Post by gr3yfox on 2009-04-11
k, i deactivated 177, then ctrl+alt+f2, went to the black screen, logged in. tried the first command, said there was no gdm to kill or something, then i did the second, and said there was no driverfile to run or something, i have the "NVIDIA-Linux-x86_64-180.44-pkg2.run" on my desktop and of course like i said before cant install it by trying to run it normally..

sorry if i sound completely noob to this, but i am hah


any other suggestions on installing the 180 driver, and fixing my flash?

EDIT: ok now i found 180 available in hardware drivers, above the 173, trying to install it at this moment, but stuck at 0%... i shall wait

EDIT2: ok, it took forever but eventually installed, not sure if its 180.44 but it is 180, whatever ubuntu shows available, as for youtube, the full screen is up to speed now, still a slight frame drop but seems better but still there, maybe because its still buffering, BUT doing any commands on the bottom bar such as volume or exit full screen takes foreverrr. like super laggy, ill place the cursor on the X but it wont highlight till several several seconds later =[

lol but thanks for the help, if there is anymore suggestions on my FLASH player, let me know 

again, much appreciation for everything so far.

---

### Post by gr3yfox on 2009-04-11
also note, i downloaded from synaptic the ubuntu restricted extras, and installed flash nonfree in terminal, i believe i uninstalled the flash before that, but in firefox, it says i have flash 10 still.

i tried turning off animations, and clicked none, which basically disabled all my compiz, i went to a video, full screen, ran fine. but i would prefer to have my compiz settings AND have flash running smooth fullscreen..

is it possible?

EDIT: i also have just noticed, when flash video (youtube) is full screened, it will run fine if the mouse cursor is not moving, but as i move it around the screen, it causes the video to lag/drop frame rate until the mouse has stopped. AND even when the mouse stops there is still a lag until it catches up with the mouse.... if that makes sense, so if i move the cursor around alot, there will be a long lag, if a little, a little lag.

and again once the cursor stops, it needs to catch up to that stop before running smooth again..

hope that made sense.. i also went to flash settings, the hardware accel is on. and went to 'local storage' and allowed unlimited which help a bit with the lag delay and all, but still have the problem..

EDIT2: now, it just went black and white (the whole firefox window, which also happened when not viewing any videos or flash content), minimized and came back and the whole window was invisible except the video box, force quit, and there was still sound from the video persisting for a minute or so... as well as sometimes having the "gray box" issue.. i assume its mainly because flash 10 and nvidia 180 are beta and things like that.. but if anyone knows to fix this problem at the moment..

it will be greatly appreciated =]

---

### Post by crowdofone on 2009-05-31
Right clicking on anything flash and unchecking "enable hardware acceleration" worked for me.

---

### Post by anchorschmidt on 2009-05-31
I had a similar problem and a complete reinstallation of the flash player worked. 
Remove it first though. Also try flash in other browsers such as Opera.

---

### Post by mykrob on 2009-07-04
> **crowdofone said:**
> Right clicking on anything flash and unchecking "enable hardware acceleration" worked for me.

thanks, that worked great for me!

---

### Post by lostinberlin on 2010-09-13
Hi, 

it seems the thread is closed but here's my 'long sought after and highly satisfying' solution - depending on your priorities. 

Turn off "desktop effects". It's as simple as that. If you can't lift without them, you could find a shortcut to turn them on or off at will, but I am quite happy without them and the video play back is fantastic. 

There you have it. Hope someone finds this useful. 

Stats: 
Kubuntu 10.04
Thinkpad W510 (1920 x 1080)

---

### Post by Samupa on 2010-10-25
yes, I have the same problem i use kubuntu 10.10 and uninstalled nvidia 173 driver and install nvidia 185 drver and the problem solved

---

### Post by sazawal on 2011-03-09
Hi guys,

I am using Ubuntu 10.10 64-bit with intel core i3 processor and ATI Radeon graphics card(ATI Mobility Radeon HD 5000 Series) on my VAIO E-series laptop. I am using adobe flash player version 10.2.152.27.
I have the same problem, my youtube video gives low frame rate in full screen, however if mouse pointer is not disturbed it works fine.

I have tried disabling hardware acceleration by right clicking the flash video, but the same problem persists. I am attaching a screenshot of my graphics card driver information.

Guys please help me out :(

---

