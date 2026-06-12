---
title: "Radeon X1950 Driver trouble"
date: 2008-12-31
forum: New to Ubuntu
---

### Post by Pat Benson on 2008-12-31
Hello ...and happy new year! :)

I've tried Ubuntu before but I'm a noob at this. Now I thought I give Kubuntu a go. 

Now I have this trouble with getting 3D work properly for me. 

Either I get 3D to work with one driver ([as this post]("https://help.ubuntu.com/community/RadeonDriver")) but then when I reboot the desktop/panels are all over the screen, with desktop effects enabled. 
The later I tried to counter with changing settings in BIOS like [this post say]("http://www.rage3d.com/board/showthread.php?t=33882145").



At the moment I use ATI driver 8.552 .. I think :-? .. according to EnvyNG 

this is how my xorg.conf file look like ... I assume something is missing .. but I can't for my life figure out how to set it, as I'm a newbie. :(  


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

```

My hardware is:
ASUS M2N -MX SE
AMD 64 X2
ATI Radeon x1950 Pro

and I have Kubuntu 8.10 KDE 4.1.3

Thankful for any help

---

### Post by chewit on 2008-12-31
Have you looked to see if your hardware has appeared in the restricted drivers list.

---

### Post by Pat Benson on 2008-12-31
hello and thank you for the reply.

Sorry but all the new terms make me confused.

I understand correct if you mean 
"K-menu > applications > System > Harware Drivers" ?

Proprietary Drivers, yes ? I get a error message when I try to install them.
[B]
Edit solved it .. beginners luck I guess ;)[URL="http://kubuntuforums.net/forums/index.php?topic=3100498.0"]

Here's[/URL] a post about it[/B]

---

