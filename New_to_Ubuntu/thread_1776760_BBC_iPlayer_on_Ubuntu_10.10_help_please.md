---
title: "BBC iPlayer on Ubuntu 10.10 help please"
date: 2011-06-06
forum: New to Ubuntu
---

### Post by baldy4eva on 2011-06-06
I have an HP G60 dual booting Ubuntu 10.10 32 bit and win7. I have installed BBC iPlayer and Adobe Air. When I launch iPlayer, it's showing up in the system monitor as using resources, but no application window is showing up. Any ideas or help would be most welcome :D

---

### Post by DogMatix on 2011-06-06
I think you need Adobe Flash plugin for your browser not Adobe Air for iplayer to work.

EDIT: Apologies. I have just discovered the iPlayer for the desktop that is indeed an Adobe Air application.

---

### Post by baldy4eva on 2011-06-06
I have the Flash plugin for the browsers I run and iplayer works fine in browsers. I'm trying to get the iPlayer application running, so I can download the tv programs and watch them offline.

---

### Post by mick222 on 2011-06-06
did adobe air install if not try running firefox as superuser gksu firefox then try to install.
It installs to /opt and you can launch it from there.It should have an entry in one of the menu's on natty so cant remember where,but It is quite a fickle little piece of software.

---

### Post by DogMatix on 2011-06-06
Just noticed on the BBC iPlayer site is states system requirements are Ubuntu 9.04 - x86 32bit. I would assume this is a minimum system requirement. But it could be a compatibility issue with newer versions of Ubuntu.

ref: [http://www.bbc.co.uk/iplayer/install](http://www.bbc.co.uk/iplayer/install)

---

### Post by baldy4eva on 2011-06-06
I've had it running on 64bit 10.10 before so I know it will run on 10.10, but I'm using 32 bit on this particular machine. I tried the gksu firefox install, and now it seems that there are some permission issues which just loop with what is shown in the screenshot when I try to change them

---

### Post by mick222 on 2011-06-06
That happened to me close firefox and restart it's working on 11.04

---

### Post by baldy4eva on 2011-06-06
Tried closing firefox and restarting. Nothing. Tried closing and restarting iplayer. Tried rebooting the laptop. Nothing. Still shows up in sysmon as using resources, but no application window.
Removed iplayer and adobe air from Software Centre, and then reinstall both using gksu firefox... Restarted and fired up the app.. Resources being used without app window

---

### Post by mick222 on 2011-06-06
if you open /opt is bbciplayer there.

---

### Post by baldy4eva on 2011-06-06
Yeah, iplayer is in /opt. Just checked the permissions on the iplayer executable in /opt/bbc iplayer desktop/bin and it seems that it's owned by root. Would this cause this problem?

---

### Post by mick222 on 2011-06-06
I don't think so mine also shows owned as root.but it gives read write permissions.

  The only thing i can think of is try to install it with the adobeair application installer open.I think i done that but still got the permission denied the first time it opened i just clicked the quit button then tried to open a download from a new Firefox window,

---

### Post by DogMatix on 2011-06-06
There is some info. on installing Adobe Air on Linux from the BBC which mentions permissions here [iplayerhelp](http://iplayerhelp.external.bbc.co.uk/help/downloading/air_linux)

---

### Post by baldy4eva on 2011-06-06
Think I may just go back to 64bit... Followed all the instructions and still no joy :( Oh well!

---

### Post by BarryM on 2011-06-16
I have just upgraded to 10.10, and found that iPlayer sometimes starts up OK, but will only play the intro sequence from a downloaded programme (downloaded before I upgraded). When it gets to the main programme it simply shows a blank screen, and will not start playing. Any ideas? Should I upgrade to 11.04 straight away, and will that solve the problem?

---

### Post by king_nerd on 2011-07-12
I have had exactly the same problem first of all with 10.10 and then with 11.04 after upgrading. Tried to fix it various ways including 1) by re-installing Air and Flash via Synaptic and 2) by following the prompts after downloading a TV programme. No difference at all. Still stops after the intro.

Then tried different pc with 10.04 and just followed the prompts. Just the same! Must be doing something obvious wrong. Any ideas gratefully received.

---

### Post by kidoko on 2011-08-25
Make sure you've uninstalled the gnu flash player - Gnash SWF Viewer

---

### Post by yellowdog1000 on 2011-08-25
I have a similar bbc problem but the root cause is that the bbc icon has been placed on a tool bar along the bottom of my screen. And, the bottom of my screen is not visible because the Ubuntu build did not set the height of my monitor correctly. This may be your problem also. A quick test would be to move your mouse all the way to the bottom. It the mouse pointer goes off screen then your screen size is wrong.

---

### Post by digitography on 2011-11-18
I have several computers that I have Ubuntu 10.10 on, and they all play iPlayer fine, but one just refuses to work. Firefox tells me that Adobe Flash needs to be installed, but it already is.
Identical hardware, all straight 10.10 install straight from the ISO and all fully up to date.
So what the heck is wrong with this one machine, that it won't play iPlayer.

Any ideas greatfully accepted.

---

### Post by coldraven on 2011-11-18
I cannot help you, I just use get_iplayer.
[http://www.infradead.org/get_iplayer/html/get_iplayer.html](http://www.infradead.org/get_iplayer/html/get_iplayer.html)

---

