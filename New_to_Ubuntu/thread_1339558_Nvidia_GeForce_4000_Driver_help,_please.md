---
title: "Nvidia GeForce 4000 Driver help, please"
date: 2009-11-27
forum: New to Ubuntu
---

### Post by guy72277 on 2009-11-27
[FONT=Arial][B]Hi,

I could really do with some help over the next couple of hours to get my Nvidia GeForce 4000 card working with Karmic[/B] on my Shuttle SB51G[B].  I've tried loads of things and done tons of forum searching over the past couple of weeks, but have not made much progress.

I am currently at the stage of having installed the recommended driver (Version 96), it shows up in System/Administration/Nvidia X Server settings.  When I click on that i get:

You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server. 

If I [/B]**run `nvidia-xconfig` as root I get the ****Nvidia driver causing a "Flickering login screen problem",** which I can fix by booting into the failsafe mode choosing root and backing up and configuring the xorg.conf file in the X11 directory. Then I'm back at the same place with "[B]Please edit your X configuration file".

Basically, I'm trying to run Boxee, (which I have successfully achieved on my Karmic Dell Inspiron 510m laptop.
[/B]
Any help would be appreciated. 

Thanks[/FONT]

---

### Post by cariboo on 2009-12-03
Check and make sure the the horizontal sync and vertical refresh rates match those of the monitor in /etc/X11/xorg.conf. 

Look for HorrizSync and VerticalRefresh

---

