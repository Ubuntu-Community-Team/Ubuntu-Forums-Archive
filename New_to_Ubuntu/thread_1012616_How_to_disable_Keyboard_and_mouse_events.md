---
title: "How to disable Keyboard and mouse events?"
date: 2008-12-16
forum: New to Ubuntu
---

### Post by umang.ece on 2008-12-16
Hi I am using ubuntu . I want to disable Keyboard/Moouse for a while and then re-enable them by command ? 
I looked at /usr/lib/X11/xorg.conf but that disabling seems to be permanent.

---

### Post by Shhnap on 2008-12-17
I think what you are looking for is a shell script that used xmodmap, setxkbmap or setkeycodes. Type in 'man xmodmap' in a terminal and get scripting. :) Either way i'm sure there is something that will do what you want. Just type in 'man -k key' for more commands.

---

### Post by LewRockwellFAN on 2011-01-09
Me too, OP. Ideally what I want is something a bit like the lock-screen doodad that I can put on the panel at the top of my desktop, that will just DO it and not bother me with the run/display/run_in_terminal choice when I click it but UNLIKE that will continue to display what's going on on the monitor. I still want to SEE what's happening - I just don't want a wandering cat or a misplaced elbow to interrupt it or execute the super-secret hotkey for the program initiating the antimatter bomb for destruction of planet earth.

---

### Post by LewRockwellFAN on 2011-01-15
Found an answer. Google "keyboard lock baby" and you'll find a bunch of links like this one:
[http://www.filecluster.com/reviews/052009/keyboardlock-lock-your-keyboard-from-unwanted-baby-action/](http://www.filecluster.com/reviews/052009/keyboardlock-lock-your-keyboard-from-unwanted-baby-action/)
For me it isn't perfect because it messes with the mouse a little more than I want it to but that maybe cause I stupidly installed Narwhal before I read the "this is an alpha and doesn't work quite right" warning.

---

