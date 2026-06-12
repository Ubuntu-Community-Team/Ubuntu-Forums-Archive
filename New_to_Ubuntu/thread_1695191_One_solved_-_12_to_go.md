---
title: "One solved - 1/2 to go"
date: 2011-02-25
forum: New to Ubuntu
---

### Post by weezyrider on 2011-02-25
Fixed the 0-DMI-table-is-broken
It was the default in the computer name box on the install CD. Probably because Ubuntu booted from CD before install. Cleared the box, and terminal looks right. 

Re: Stellarium.
I've reinstalled Ubuntu. Stellarium still won't run, but now I've found what could be the problem. Stellarium says there is no viewer available to open the program. 

So this is a new question. Is this due to the ATI card, or can I install another viewer? If so, which one?
Thanks

---

### Post by bug67 on 2011-02-25
How did you install Stellarium?  From the repos?

---

### Post by seawolf167 on 2011-02-25
You could be missing dependencies if you compiled from source - here is a quote from their user guide

[I]"Check if your distribution has a package for Stellarium already - if so you&#8217;re probably
best off using it. If not, you can download and build the source. See the wiki for detailed
instructions."[/I]

So I'd check the Ubuntu Software Center or do a 

```
sudo apt-get install stellarium
```

---

### Post by weezyrider on 2011-02-25
I installed it from the software center. It's checked as installed, too.  I looked in Synaptic and that's where it said there was no viewer installed.   I've got other programs that say they are installed, but these are not in the menu.  FF is refusing to see Adobe Flash at all. Google Chrome is having no problem.  Thanks

---

### Post by weezyrider on 2011-02-26
Been reading - finally found this:


Using default graphics system specified at build time:  raster 
 ------------------------------------------------------- 
[ This is Stellarium 0.10.5 - [http://www.stellarium.org](http://www.stellarium.org) ] 
[ Copyright (C) 2000-2010 Fabien Chereau et al          ] 
 ------------------------------------------------------- 
Writing log file to: "/home/weezyrider/.stellarium/log.txt" 
File search paths: 
  0 .  "/home/weezyrider/.stellarium" 
  1 .  "/usr/share/stellarium" 
Config file is:  "/home/weezyrider/.stellarium/config.ini" 
Qt GL paint engine is:  "OpenGL" 
drmRadeonCmdBuffer: -22. Kernel failed to parse or rejected command stream. See dmesg for more info.
 So now what do I do?
Thanks

---

