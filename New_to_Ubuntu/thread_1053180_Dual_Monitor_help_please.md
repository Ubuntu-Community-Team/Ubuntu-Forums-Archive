---
title: "Dual Monitor help please"
date: 2009-01-28
forum: New to Ubuntu
---

### Post by scudrunner on 2009-01-28
Greetings Ubuntu experts,
Total noob here.....
I finally have that beautiful Heron on my laptop's desktop and I "think" everything is working OK.

My problem lies with monitors. When I am running WinXP Pro and have my second monitor plugged in, everything is fine, can move everything back and forth between the two and even can have different wallpaper backgrounds, no problems.

When I start Ubuntu, with the second monitor disconnected, Hardy is on the laptop monitor. If I turn the PC off, plug the second monitor in and restart, Hardy is on the second monitor! (I would think it would still be on the laptop but it's not)

Seeing that it obviously knows how to use both, depending upon whether the second one is plugged in or not, how do I get them both to be on at the same time and work like Windows where I can drag stuff back and forth between the two??

The driver in the laptop is Microsoft NVIDIA GeForce2 Go which it is obviously using or I would have blank screens. (when I look at Hardware Drivers, the only thing there is "NVIDIA accelerated graphics driver" which is not enabled and Not in use, which makes sense since it is not a 3D device.

This is what is in my xorg.conf file:
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

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

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Synaptics Touchpad"
EndSection

Any help appreciated.

---

### Post by cozmicharlie on 2009-01-28
You should have menu>administration>NVIDIA X server settings -open it and you can configure the monitors.  Make sure to check the bios - some have a switch for allowing dual monitors make sure it is enabled.  I have attached my xorg.conf file as an example.

---

### Post by scudrunner on 2009-01-28
I am trying to find it. Will post back.
Am puzzled about one thing though, if you're talking about the laptop's BIOS (is there a separate one for Ubuntu?)it is obviously setup for dual monitors as I am using them in Windows.

---

### Post by Sarai the Geek on 2009-01-28
You've probably tried this, but...

System>Administration>NVIDIA X Server Settings (or similar)

If you click on the side tab that says X Server Display Configuration, then the button "detect displays" it will bring up your lists of displays and allow you to configure them as you wish. It's not exactly intuitive but if you spend a little time playing with it you can get it the way you want. This is what I had to do with mine, but I'm using intrepid, perhaps it's a little more roundabout with hardy. You should consider upgrading... :D

---

### Post by scudrunner on 2009-01-28
Yea, tried something like that...it's under System > Preferences > Screen Resolution but it doesn't detect anything.
I'm still trying to find cosmicharlie's files...
I found one, NVIDIA X Server Settings (350 bytes), tried to open it and got an error...Failed to execute child process "/usr/bin/nvidia-settings" (No such file or directory)
That puts it a long way from menu>administration>NVIDIA X server settings which I think are in the file system files.

---

### Post by Locke_99GS on 2009-01-28
Make sure the nvidia restricted drivers are installed for your video. The NVidia Xconfig utility should be installed alongside the drivers.

When you are able to use the nvidia xconfig utility, make sure you open it with *gksu* or it won't be able to save changes to your xorg.conf.

---

### Post by scudrunner on 2009-01-28
Locke,
Thanks for the reply.
Installing a Nvidia .run file. Suppose to be the legacy driver(s) that I am hoping will make something work. 
I just can't figure out why I have to do this when both monitors work....just not together.

---

### Post by Garyhans on 2009-01-28
I have NVIDIA..  6600GT.. I used.. EnvyNG.. then Nvidia-settings..  set it up as an Xserver.. but you have to use.. sudo.. Nvidia-settings for permanant change.. I preferred xserver over. cinema.. which seemed to respond.. to my liking..

---

### Post by scudrunner on 2009-01-28
Thanks, but this is all way over my head...
I thought the .run file was like a .exe file in Win and it would just install to the proper location. Nope...
Trying to Google the answer...

---

### Post by Garyhans on 2009-01-28
EnvyNG is the best way to go.. in my opinion.. hasn't failed me yet.

---

### Post by scudrunner on 2009-01-28
What do I do, type EnvyNG in a command line?
I don't have any kind of special graphics card, it's just propietary MS Nvidia, old in fact.

---

### Post by cozmicharlie on 2009-01-29
Sorry for leaving you hanging - I got real busy at work.

The NVIDIA xserver settings are not in your files but should be in your menu.  If you go to the menu under system>administration> you should see an entry for Nvidia Xserver settngs.  if it is not then than open Synaptic and search for NVDIA - there should be a package called "NVIDIA-Settings" go ahead and install it (note:  all this assumes you are running Intrepid).  you also may need toinstal the nvidia-common.  Also, if you want to use EnvyNG you can install that from synaptic instead (I don't think you need both).  Also, I assume you have installed any restricted drivers - if not then go ahead and install them - in the menu go to sytem>administration>Hardware Drivers and you should see your driver listed.  It is probably already activated but just check and make sure.

As per the bios - you may or may not need to do anything.  Some bios have a setting for dual monitors and some don't (for example mine did not).  All I wanted was for you to check and make sure your bios did or did not have the switch.  You open the bios when you first turn on your computer - you should open it by hitting f2, esc, del, f10 - one of those should open it (it should say how to open it on the screen as soon as you start (or check your computers manual).  Once in the bios go through the basic settings and see if there is anything that says "dual monitors".  If not then you are good to go if so then you need to change the settings.  If you had a dual monitor working in windows then most likely you don't have to change anything and I would not even bother checking the bios. 

Hope this helps

---

