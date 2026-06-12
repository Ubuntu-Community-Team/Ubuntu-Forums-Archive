---
title: "screen resolution on a tv using (sg33g5b)"
date: 2009-05-07
forum: New to Ubuntu
---

### Post by darkjunkie on 2009-05-07
Hello, 

I installed ubuntu to my new system yesterday but I had a number of problems getting it to work with my TV via HDMI it would boot up but only half the screen was the desktop the rests was horrid lines and stuff and the half that was the desktop was a squished up and unreadable..

So I plugged in a spare 17" monitor via VGA and restarted everything worked fine both the 17" monitor and the tv loaded up at the same time and looked perfect, but silly me.. I felt the need to try and bump up the resolution when I did this the screen was alright but the tv gave me an error "Video not supported". when I put the resolution back to its previous setting it returned to reverted back to the state whereby half the screen worked and the other half was a mess and I can't seem to fix this no matter what res I choose for the tv?

My setup;
SG33G5 barebones
Intel Core 2 Duo E8400 Socket 775 (3.0GHz)
Kingston KVR800D2N5 2GB
Random 160gig sata HHD
Philips 26PFL5522D/05 HD LCD TV

I might also point out I not installed any drivers and this system isnt connected to the internet yet (waiting for my wireless card to show up), the drivers that came with the barebones from shuttle are all for windows and I can't find any linx / ubuntu drivers on their website?

---

### Post by cariboo on 2009-05-07
It sounds like a video drivers problem. You can install the restricted video drivers two ways, you need a network connection using either method.

[list]
[1] The easy way, once you have a network connection you will be notified that there are restricted video drivers available. Go to System-->Administration-->Hardware Drivers, the drivers will automagically be installed

[2] The hard way, go to the graphics adapters manufacturers web site [ATI]("http://support.amd.com/us/gpudownload/Pages/index.aspx") here and [Nvidia]("http://www.nvidia.com/object/unix.html") here.
[/list]

You will also have to install the build-essential package, which is in the repositories, you can use Add/Remove Programs or Synaptic Package Manager to install it.

---

### Post by overdrank on 2009-05-07
I agree with cariboo907 and if your system has the GMA 3100 integrated graphics with Jaunty 9.04 you may look at the intel graphics link in my signature.

---

### Post by darkjunkie on 2009-05-07
Ok, so I've hooked myself upto the net and gone:

System-->Administration-->Hardware Drivers its hangs for about 10seconds checking for drivers then displays a windows say with 2 empty boxes and a message at the top saying

"No proprietary drivers are in use on this system"

I am off to those websites now and I'll give it ago doing it the hard way :(

---

### Post by darkjunkie on 2009-05-09
I've reached breaking point now I've spent 4 nights now trying to get this to work and I simply cannot do it.. I've read 50+ threads about this issue and tried just about all the suggestions many of which have meant i've had to reformat and start again and nothing has worked :(

I don't understand what I am doing wrong, the only install for intel driver I could get to run simply said that they were not the lastest and didnt install and my xorg.conf doesnt have anything usefull in it and everytime i try to change it, it breaks everything.

---

### Post by Eberhard on 2009-05-09
Seems you have used a long time to figure it out so i know it may sound silly but have you tried to disable compiz(system->pref.->appearance - visual effects = none). I've had resolution problems with an external monitor using compiz and disabling compiz worked for me.

---

### Post by darkjunkie on 2009-05-09
seems unlikely that would be the problem, altho I tryed it.

the small and short of it is that I still don't seem to have graphic drivers my xorg.conf file is basically empty and has no screen resolution or driver information in it.. my tv resolution is 1366x768 but the closes I can get is 1300x768

It keeps coming around to people saying I have to compile the drivers manually from the intel website but I can't make heads or tales of how to do this since the resources they tell me to download come up saying unkown protocal. 

I am going to spend 30mins more on this and if I can't get it to work I guess I'll have to buy windows. :confused:

---

### Post by cariboo on 2009-05-09
I wasn't paying attention to your first post, if you are running Jaunty or Koala there are several solutions to your problem. Have a look at [thread=1130582]The Jaunty Intel Performance Guide[/thread] and [thread=1136738] How to Fix Intel Video in Jaunty[/thread] (Alternate way) and the solution I use for my media center pc to fix video tearing problems, [X updates]("http://edge.launchpad.net/~ubuntu-x-swat/+archive/x-updates/").

I have my media center pc connected to a Samsung 32" HiDef LCD, the native size is 1360X768. It is based on an Intel Atom motherboard with the 945 video chipset.

---

### Post by kdiddy on 2009-05-09
I had to disable the xrandr plugin in gconf-editor. I think
the plugin is used to detect info about the monitor . When I changed the resolution I would get the same message video not supported. I have 46 " samsung , using hdmi port on ASUS motherboard 

command gconf-editor

go to apps>>gnome_settings_daemon>>plugins>>xrandr and disable it 

hope it helps

---

