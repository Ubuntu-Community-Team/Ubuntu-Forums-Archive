---
title: "X won't start...again."
date: 2009-04-17
forum: New to Ubuntu
---

### Post by asuastrophysics on 2009-04-17
i restarted my computer and now x won't start. 

things i tried at the shell:

sudo dpkg-reconfigure -phigh xserver-xorg
sudo /etc/init.d/gdm restart
didn't work.

aticonfig --initial
sudo /etc/init.d/gdm restart
didn't work.

i also tried booting into recovery mode and selecting "try to fix x server"
didn't work. 

any ideas?

---

### Post by asuastrophysics on 2009-04-17
i also have no internet access. who designed the stupid tty1 thing? 
what is the point in having the "dpkg Repair broken packages" option in recovery mode if TTY was never designed with internet support?
if i try to fix broken packages, it says "could not resolve host blahblahblah", meaning no internet. 

to confirm this, i did "ping www.google.con"
"unknown host "www.google.com""

so i did this
"sudo ifconfig eth0 up"   OK
"sudo ifconfig lo up"     OK

and then i pinged google
....and....nothing. 

So right now, i have 
(for no reason) no internet 
(for no reason) no X server
no cdrom drives (i need to find an IDE cable; apparently impossible in a college town)
no ALSA server (no sound, but that was my own doing for updating sound drivers) 

the machine is useless. bricked. does anyone know how to help me with just the internet? if i can get that to work, i can fix everything else.

---

### Post by swoll1980 on 2009-04-17
Go into the recovery terninal.


```
cd /etc/X11
``` this will put you in the right directory. 
```
ls
``` this will list the files in the directory. Look for xorg.conf.backup. If it's there do ```
sudo mv /etc/X11/xorg.conf.backup /etc/X11/xorg.conf

``` This will replace the xorg file with the back up. Hopefully that works. If you have several backups try the oldest one first.

---

### Post by asuastrophysics on 2009-04-17
thanks for the tip.

i tried every single backup that i had. after every one, i would do 
```
sudo /etc/init.d/gdm restart
```
and then hit CTRL+ALT+F8 

nothing. all 19 backups failed. i have no idea why this isn't working...
](*,)](*,)](*,)](*,)](*,)

can someone show me what an xorg.conf looks like with the VESA drivers enabled?

---

### Post by asuastrophysics on 2009-04-17
guys i am running out of ideas. i just need to know how i can enable my ethernet controller ETH0

if i can do that, i can fix it, because it's just a simple apt-get install ati whatever. does anyone know how to enable an ethernet controller from shell? 

obviously sudo ifconfig eth0 up is wrong. what other codes are there?

---

### Post by swoll1980 on 2009-04-17
> **asuastrophysics said:**
> guys i am running out of ideas. i just need to know how i can enable my ethernet controller ETH0

if i can do that, i can fix it, because it's just a simple apt-get install ati whatever. does anyone know how to enable an ethernet controller from shell? 

obviously sudo ifconfig eth0 up is wrong. what other codes are there?

It should work in the shell if it worked in the GUI
Try ```
sudo /etc/init.d/networking start
``` try using you text based web browser```
 w3m google.com
``` if it takes you to a command line version of google then you know you have internet

---

### Post by asuastrophysics on 2009-04-17
i got it to work using this:
```
/etc/X11$ xinit
```
i then had a really crappy screen in front of me w/ a terminal.
```
metacity
```
the terminal now has a frame
```
gnome-panel
```
```
x-session-manager
```
```
gnome-settings-daemon
```

i now have a desktop. magically and illogically, internet now works. 

i am now upgrading to jaunty, hoping that even having really crappy ATI support will be better than the shell i was using.

---

### Post by swoll1980 on 2009-04-17
> **asuastrophysics said:**
> i got it to work using this:
```
/etc/X11$ xinit
```
i then had a really crappy screen in front of me w/ a terminal.
```
metacity
```
the terminal now has a frame
```
gnome-panel
```
```
x-session-manager
```
```
gnome-settings-daemon
```

i now have a desktop. magically and illogically, internet now works. 

i am now upgrading to jaunty, hoping that even having really crappy ATI support will be better than the shell i was using.

With what you just described it sound like ```
startx
``` would have got you going fine.

---

### Post by asuastrophysics on 2009-04-23
> **swoll1980 said:**
> With what you just described it sound like ```
startx
``` would have got you going fine.

hahaha. i didn't know what the script command was to launch everything in sequence, 
plus i didn't know which application or process was causing it to crash, so i just  manually launched basic processes in sequence, narrowing down the list as to what was causing the problem. 

EDIT *****-> It turns out that i had the FGLRX driver installed, which is NOT COMPATIBLE with jaunty at this time. 

no proprietary ATI graphics drivers work with jaunty as of 4-23-09. 
i just learned this. 
i also used to think that fglrx was open source, this is why it took me a bit of reading to figure out my dilemma. all up and running now! :guitar:

now if i could only enable compiz with this open-source ATI driver.......

---

