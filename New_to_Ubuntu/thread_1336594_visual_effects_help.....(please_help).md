---
title: "visual effects help.....(please help)"
date: 2009-11-24
forum: New to Ubuntu
---

### Post by techno_909 on 2009-11-24
hello guys m new to ubuntu i actually wanted to try ubuntu bcoz of it graphics and hassel free usage now i wanted to enable visual effects but unable to do that.......

on visual effects tab when i click normal settings it start searching for drivers and after that screen slightly blinks and give me a message desktop effects cannot be enabled 

i even updated my drivers still nothing 

my video driver:- m suing ubuntu 9.10 karmic koala

VIA Technolohies, Inc. CN896/VN896/P4M900 [Chrome 9 HC] (rev 01)

and i have dual booted ubuntu with windows xp pro sp2

plz plz help me step by step guide for enabling visual effect will be very helpful coz m using ubuntu for 1st time 

thnx in advance plz do tell me if u need any further info or specs.......

---

### Post by nitstorm on 2009-11-24
go to application--> add/remove programs  and search for ccsm and download and install it, once its done, right-click on ur desktop and go to change desktop background , under the visual effects tab click on high, then click close, after that  u should find compiz settings manager or something similar to it  in system -->preferences i guess, click on it and enable whatever visual effects u want ,

hope i was a lil useful, cheers ;)

oh btw, by visual effects, i take it u mean eye candy, if its something else i am sorry but do post back, some one will help u out..

---

### Post by techno_909 on 2009-11-24
nope i have tried it i downloaded ccsm and even emerald settings manager but my prob is that its not enabling visual effects u said after downloading ccsm click in high but it is not turning it on it just giving a message desktop effects not enabled after searching for drivers...........ne wasy tyvm for helping hope some1 will help me finding the exact solution.......

---

### Post by Bölvaður on 2009-11-24
omg nitstorm you must read what the person is writing.


as for the OP.
I am not sure if your graphic card is powerful enough or the drivers are up for it. I pretty much know nothing about this to be honest. 

but.... according to this thread [http://ubuntuforums.org/showthread.php?t=1196831]("http://ubuntuforums.org/showthread.php?t=1196831") you should check your xorg.conf

press alt+F2
```
gksu gedit /etc/X11/xorg.conf
```

now according to that same thread this was the trick
```

Section "Device"
Identifier	"Configured Video Device"
Driver "openchrome" 
EndSection 
```

---

### Post by Sealbhach on 2009-11-24
Hi, run the command

compiz-check

in a terminal and see what the output is.

.

---

### Post by ajgreeny on 2009-11-24
> **Sealbhach said:**
> Hi, run the command

compiz-check

in a terminal and see what the output is.

.
You will need to install the shell script file from Forlong to run that command.

See [here]("http://forlong.blogage.de/article/pages/Compiz-Check").

I suspect, however that your via graphics card does not support compiz for now, at least.

---

### Post by Tholley on 2009-11-24
Here are some usefull tips for beginners...
 
[http://www.johannes-eva.net/](http://www.johannes-eva.net/)
 
[http://ubuntuforums.org/showthread.php?t=766683&highlight=HARDWARE+LIST](http://ubuntuforums.org/showthread.php?t=766683&highlight=HARDWARE+LIST)
 
[http://sites.google.com/site/easylinuxtipsproject/Home](http://sites.google.com/site/easylinuxtipsproject/Home)
 
Allot of GOOD info!

---

### Post by techno_909 on 2009-11-25
thnx very much to all of u i'll try wat all of u have suggested and report back after hit and trial rounds hope something will work for me thnx everybody for giving a chunck of yur precious time.....

after i run the compiz-check command in terminal the out was like this 

distribution: ubuntu 9.10
desktop environment: gnome
graphic chip: VIA Technologies, Inc. CN896/VN896/P4M900 [Chrome 9 hc] (rev 01)
driver in use: openchrome
rendering method AIGLX
checking if it's possible to run compiz on your system... [skip]

checking for hardware/setup problems...     [skip]

atleast one check had to be skipped:
Error: openchrome driver in use

idk wat does this error means but any1 some1 plz help

---

### Post by mlissner on 2010-02-05
I have this same integrated video card. Looks like it doesn't support compiz. Does anybody have any good recommendations for a simple video card that I can drop in my machine and have it work?

---

