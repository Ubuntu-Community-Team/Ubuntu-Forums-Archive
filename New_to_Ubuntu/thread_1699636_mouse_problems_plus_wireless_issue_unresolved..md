---
title: "mouse problems plus wireless issue unresolved."
date: 2011-03-03
forum: New to Ubuntu
---

### Post by williamsld8 on 2011-03-03
so i recently posted about a problem i was having involving my wireless situation. im sure you could find that just by searching this forum for my user name. its been up for sometime and only has one reply, which was from myself. but now i have another issue which i hope some users will be more eager to help with. i have a wired usb mouse i borrowed from a friend of mine. its a gaming mouse with all the buttons all over it. i plugged in the usb plug and after about 3 seconds was able to move and click with said mouse. thank jesus my touchpad days are gone. then all of a sudden my computer was frozen. wrong. i was able to move the mouse but not click on anything. the mouse moves but nothing i click on responds. frozen. still wrong. this happens with the mouse and touchpad, until i UNPLUG the mouse and use the touchpad exclusively. then everything returns to normal. i plug the mouse back in. everything is fine for 10 seconds. then history repeats itself. am i stuck using this god awful touchpad?

---

### Post by Dutch70 on 2011-03-04
Welcome to UF williamsld8.

 Have you tried a different mouse? or when you plug it in, do you have time to check for additional drivers? I think it's under system>admin>additional drivers, but can't be sure. I'm on Linux Mint at the moment.

---

### Post by williamsld8 on 2011-03-05
no i do not have time to check for additional drivers. i did however pull down the menu, then click on it and immediately plug in the mouse, which means it was plugged in and active when the computer was searching for available drivers, and nothing came up. and i have not come across another mouse i can try as of yet.

---

### Post by wep940 on 2011-03-06
You'll need that mouse plugged in before you start searching for additional drivers. Use your touchpad to navigate when the mouse isn't working so it can search for drivers. I doubt it will find any, but it's worth a try. I would also try disabling the touchpad altogether (just temporary - be sure you know how to set it back before you disable it!)  prior to trying to use the mouse to see if that works or not. You don't have any other mice plugged in, right?
 
Since this is USB mouse, please do the following as well:
 
- open a terminal window (applications/accessories/terminal)
 
- type:
 
lsusb <press enter>
 
post the output back here.
 
What brand and model is the mouse? Have you tried an internet search engine using Linux and the brand/model of mouse? It might turn some things up for you.

---

### Post by williamsld8 on 2011-03-06
number one: i had it plugged in when the driver search began. 
number two: the touchpad doesnt work either when the mouse is plugged in. i can move butcannot click on anything, same as with the mouse. so when its plugged in nothing can be done.
number three: i went into the mouse properties and although i cannot disable touchpad altogether, i can disable the ability to click by tapping the touch pad, which i did, so now the clicking only works by actually clicking the touchpad mouse button. and so far this has allowed my mouse to work perfectly fine. and its a rat 7 gaming mouse.

---

### Post by williamsld8 on 2011-03-06
looks like i spoke too soon. it works for a longer period of time now, but still has the same end result

llance@lance-HP-Mini-210-1000:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 064e:f100 Suyin Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
lance@lance-HP-Mini-210-1000:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 015: ID 06a3:0ccb Saitek PLC 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 064e:f100 Suyin Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
lance@lance-HP-Mini-210-1000:~$ 


this is the terminal result. the first one was with the mouse unlpugged the second was with the mouse plugged in.

---

### Post by wep940 on 2011-03-07
The problem is in the mapping of the buttons. There is a thread about this on launchpad and I've included only the important part from that thread below:
 
```
[David Collins]("https://launchpad.net/~sofoxx") wrote on 2010-12-14: [#23]("http://ubuntuforums.org/ubuntu/+source/xserver-xorg-input-mouse/+bug/615892/comments/23") 
Yarro:
Steps to get RAT 7 working:
1) Open terminal
2) Type (without quotes) "sudo gedit /etc/X11/xorg.conf" (Enter password if needed)
3) In the text file that opens up, add this to the bottom:
Section "InputClass"
        Identifier "Mouse Remap"
        MatchProduct "Saitek Cyborg R.A.T.7 Mouse"
        MatchDevicePath "/dev/input/event*"
        Option "ButtonMapping" "1 2 3 4 5 6 7 2 9 10 11 12 0 0 0"
EndSection
4) Save file
5) Restart computer (or just restart the X server if you know how)
6) Use mouse!
Above solution is based on Mitch Walker's comment #17.
```
 
EDIT:  You may need to create the entire xorg.conf file if none exists.  There are some posts in the forum about how to do so.

---

### Post by williamsld8 on 2011-03-10
so if i were to plug in a standard two button and one scroll wheel mouse like any regular modern mouse, would this mapping still need redone or would it have a better chance of just working right away?

---

### Post by wep940 on 2011-03-10
A regular mouse should work just fine "out of the box".  The problem is specific to the rat 7 and how the buttons are mapped.

---

