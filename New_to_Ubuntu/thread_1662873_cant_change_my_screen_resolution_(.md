---
title: "cant change my screen resolution :("
date: 2011-01-08
forum: New to Ubuntu
---

### Post by elli0t0 on 2011-01-08
I downloaded Ubuntu 10.10 today.. Everythings fine, except I cant get the resolution size i want :/

When I open Monitor Preferences, the best option I get is 800x600. I've had a little search and this seems to be a common problem. I tried as many solutions as I could find, but they all need me to use Xorg.conf

The problem here is terminal never seems to be able to find it. If i open it in gedit, is completely blank, i dont think it exits. I can't find the folder it should be in..

Can anyone help me with this please? :)

---

### Post by Jeffreytooker on 2011-01-08
I had the same problem.  Since you are in 10.10, can you see the tool bar at the top of the screen?  If you can that is good.  Find your manual for your monitor. If you can not find the manual look for it online.  Look up desired resolution for your monitor.  Then go to the top tool bar on your monitor. Left click system/preferences/monitors.  This should get you to resolution choices.  Choose the resolution for your monitor.  If you can not find the exact resolution, try something just a bit lower than desired resolution.  You may have to make a couple of tries. YMMV

Jeffrey

> **elli0t0 said:**
> I downloaded Ubuntu 10.10 today.. Everythings fine, except I cant get the resolution size i want :/

When I open Monitor Preferences, the best option I get is 800x600. I've had a little search and this seems to be a common problem. I tried as many solutions as I could find, but they all need me to use Xorg.conf

The problem here is terminal never seems to be able to find it. If i open it in gedit, is completely blank, i dont think it exits. I can't find the folder it should be in..

Can anyone help me with this please? :)

---

### Post by Jeffreytooker on 2011-01-08
Older monitors are sometimes harder to set up because of some driver problems.

Jeffrey

---

### Post by Argosse on 2011-01-09
what type of video card are you using and what driver pkgs installed i just got my old radeon 9550 working with dual monitos    i know theres a command to force xserv to use        /etc/X11/xorg.conf and when i get on pc ill show you my conf file

---

### Post by elli0t0 on 2011-01-09
My video card is Sis 771/671 PCIE, i haven't installed any additional drivers

I've read that i can edit the xorg.conf file to solve the problem, but my xorg.conf file doesn't exist
whenever i try to configure it in terminal, it produces a fatal error :/

---

### Post by Argosse on 2011-01-11
would you possibly be able to sudo gedit and put this in and change it to your needs then save as /etc/X11/xorg.conf



```


Section "Device"
 Identifier "ATI radeon 9550"
 Driver "ati"
EndSection


```


Thats what mine looks like. And that fixed my GL and HW Accel probs.

---

### Post by realzippy on 2011-01-11
@Argosse
Your file is for ATI,OP has VIA/SIS graphics."change to your needs" means "create your own"...kinda hard stuff since we are in
asolute beginner's talk   ;-)



*This* xorg.conf file should work with your graphics:
Run in terminal:

```
gksudo gedit /etc/X11/xorg.conf
```

..an empty file opens,paste this in:

```
Section "Device"
 Identifier "Configured Video Device"
 Driver "openchrome"
EndSection
Section "Monitor"
 Identifier "Configured Monitor"
 Option "DPMS"
 HorizSync 28-80
 VertRefresh 43-60
EndSection
Section "Screen"
 Identifier "Default Screen"
 Monitor "Configured Monitor"
 Device "Configured Video Device"
 DefaultDepth 24
 SubSection "Display"
  Depth 24
  Modes "1280x1024"
 EndSubSection
EndSection
Section "ServerLayout"
Identifier "Default Layout"
Screen "Default Screen"
EndSection
```

If you want an other resolution than 1280x1024,change it in the line:
"Modes 1280x1024" to your needs,eg "Modes 1024x768";close the file
**saving** changes.Reboot & pray.
If (don't think so) you cannot boot afterwards,boot in recovery mode,drop to shell,log in and delete the xorg.conf:
```
sudo rm /etc/X11/xorg.conf
sudo reboot
```

---

### Post by Nikola Georgiev on 2011-03-12
> **realzippy said:**
> @Argosse
Your file is for ATI,OP has VIA/SIS graphics."change to your needs" means "create your own"...kinda hard stuff since we are in
asolute beginner's talk   ;-)



*This* xorg.conf file should work with your graphics:
Run in terminal:

```
gksudo gedit /etc/X11/xorg.conf
```..an empty file opens,paste this in:

```
Section "Device"
 Identifier "Configured Video Device"
 Driver "openchrome"
EndSection
Section "Monitor"
 Identifier "Configured Monitor"
 Option "DPMS"
 HorizSync 28-80
 VertRefresh 43-60
EndSection
Section "Screen"
 Identifier "Default Screen"
 Monitor "Configured Monitor"
 Device "Configured Video Device"
 DefaultDepth 24
 SubSection "Display"
  Depth 24
  Modes "1280x1024"
 EndSubSection
EndSection
Section "ServerLayout"
Identifier "Default Layout"
Screen "Default Screen"
EndSection
```If you want an other resolution than 1280x1024,change it in the line:
"Modes 1280x1024" to your needs,eg "Modes 1024x768";close the file
**saving** changes.Reboot & pray.
If (don't think so) you cannot boot afterwards,boot in recovery mode,drop to shell,log in and delete the xorg.conf:
```
sudo rm /etc/X11/xorg.conf
sudo reboot
```

I got another type of video card (some kind of Intel built-in to the motherboard).

Tried that.
I got a "Ubuntu is running in low graphics mode. (EE) No devices detected" message and a couple of options to chose from:

1. open ubuntu with low-end graphics just one time
2. troubleshoot
3. change settings
and something else, which I don't remember

---

