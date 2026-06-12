---
title: "terminal white screen of death after Nvidia driver update."
date: 2009-08-22
forum: New to Ubuntu
---

### Post by Jonas thomas on 2009-08-22
I just got done uploading the 96.43.13 driver for my Geforce4 MX420 card run 32 Bit 8.04

I have this real weird going on when I have the normal Visual effects enabled.  Everything seems to be working fine great except when I open a terminal session. I get white and nothing else...

It googled and it seemed that this was an big issue in 2007 with various hacks to fix it.
Offhand, does anyone have a 2009 solution for this??

---

### Post by Penguin Guy on 2009-08-23
> **Jonas thomas said:**
> I just got done uploading the 96.43.13 driver for my Geforce4 MX420 card run 32 Bit 8.04

I have this real weird going on when I have the normal Visual effects enabled.  Everything seems to be working fine great except when I open a terminal session. I get white and nothing else...

It googled and it seemed that this was an big issue in 2007 with various hacks to fix it.
Offhand, does anyone have a 2009 solution for this??
On [[COLOR="Blue"]this page[/COLOR]]("http://ubuntuforums.org/showthread.php?t=422520") somebody suggests running [COLOR="Green"]sudo apt-get install nvidia-glx[/COLOR].

---

### Post by Jonas thomas on 2009-08-27
Sorry about taking some time to get back on this.  I was hoping for some response from Nvidia... But none so far from Nvidia on this issue.( I got spoiled by a quick reponse on my first question to them.

I was able to engage my special effects momentarily but that only worked within the same session when I:  sudo apt-get install nvidia-glx.  Unfortunately everything got hosed when I re-booted.  
I tried running glxgears (which was running well) now gives me this message:
jonas@Ubuntu4:~$ glxgears
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't get an RGB, Double-buffered visual
jonas@Ubuntu4:~$ 

When I went to system->adminstration->hardware driver.  My Nvidia proprietary driver is no-where to be seen. Yikes..... 

I saw somewhere something about some tweaks to the xorg-config for LCD screens. I think I might try to re-install the Nvidia driver and try that. Although I'm real curious to see what happens when remove nvidia-glx and try to reboot. free to chime in...

[Edit]
This seemed to fix things up just fine.
[http://forum.compiz-fusion.org/showthread.php?t=7431&highlight=white+terminal]("http://forum.compiz-fusion.org/showthread.php?t=7431&highlight=white+terminal")
In case the link goes away..
> That's a common problem on nvidia. Run
Code:

 sudo nvidia-xconfig --add-argb-glx-visuals -d 24

and restart X

---

