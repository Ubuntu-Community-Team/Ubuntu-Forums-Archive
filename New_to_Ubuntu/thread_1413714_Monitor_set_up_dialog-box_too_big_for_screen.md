---
title: "Monitor set up? dialog-box too big for screen"
date: 2010-02-22
forum: New to Ubuntu
---

### Post by penguinv on 2010-02-22
I have 9.10. I just upgraded from 9.04
This is not a new problem but since I can use the system anyway and I didnt quite know how to describe it I've let it go.

What happens: I am upgrading and there is window that comes up to tell me what is going on. I clicked on >Terminal so I can have something to watch as the process goes by.

When it comes up it is too big for the screen. I cant see the bottom of the window. This is not an isolated occurrence.

PS: and below, I am putting in tags, and UF makes suggestions for the tag, I cant see the suggestions because they go below the screen.

This is a Dell monitor, Ultrascan P991. It's about a 20" I think.

Thanks.

And while you wait....    :popcorn:

---

### Post by ubudog on 2010-02-22
Might want to mess around with the resolution settings.  Go to System>Preferences>Display and you should be able to change the settings of the monitor resolution.  That should work.  Hope that helps! :popcorn:

---

### Post by van_Zeller on 2010-02-22
or this:

[http://www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html#more-3469](http://www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html#more-3469)

---

### Post by halitech on 2010-02-22
if you can't change the resolution, open a terminal and run
```
lspci
```and post the info here so we can see what video card you have.

---

### Post by mahiyar on 2010-02-22
Another thing you might want to check is allocated video memory in the BIOS (if this is on-board graphics card), go in BIOS and change it to max, for me it was 8 MB, I found this to be the problem when all the regular methods failed.

---

### Post by 3rdalbum on 2010-02-22
You can move windows around by holding down Alt and dragging them. Looks like your screen resolution needs some tweaking.

---

### Post by penguinv on 2010-02-28
> **ubudog said:**
> Might want to mess around with the resolution settings.  Go to System>Preferences>Display and you should be able to change the settings of the monitor resolution.  That should work.  Hope that helps! :popcorn:

Want you to know I tried that. I'm on a different (smaller physically) monitor for a while. It gives me a higher resolution.

I'll try the rest later. Thanks for the responses.


Just another penguin

---

### Post by penguinv on 2010-02-28
> **3rdalbum said:**
> You can move windows around by holding down Alt and dragging them. Looks like your screen resolution needs some tweaking.


AU CONTRAIRE: (as if I didnt know how to grab the top line of a window)
I cant move a dialog box that is "bigger than my screen". For example, the Preferences box in XCHAT. I cannot OK it.

---

### Post by penguinv on 2010-02-28
> **halitech said:**
> if you can't change the resolution, open a terminal and run
```
lspci
```and post the info here so we can see what video card you have.

Thanks for the good words _but I DO want to hear a solution_  
lulz

OK here's the output of that command:
00:00.0 Host bridge: VIA Technologies, Inc. VT8378 [KM400/A] Chipset Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237/VX700 PCI Bridge
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
01:00.0 VGA compatible controller: VIA Technologies, Inc. KM400/KN400/P4M800 [S3 UniChrome] (rev 01)


NOTE: this other monitor _also a Dell, maybe a 13" gets a higher resolution, 1024 x 768. (Recall the 20" Dell gets bigger text, a smaller resolution and dialog boxes get too big to see the whole window (of the dialog box).)

(I am still learning to post better. I should have posted the max-resolution and that I had already tried going to
    System> Preferences> Display 
before I posted. 
Thanks again for your patience.)

---

### Post by 3rdalbum on 2010-02-28
> **penguinv said:**
> AU CONTRAIRE: (as if I didnt know how to grab the top line of a window)

I'm not talking about the titlebar of the window. You hold down Alt and drag the contents of the window itself. It has always worked for me. And unlike dragging the titlebar, you can drag the window so far upwards that the titlebar is off the screen. This may help you get to the OK button at the bottom of the window.

Alt-dragging is an essential skill for netbook owners.

---

### Post by halitech on 2010-03-01
you can try the info here

[http://ubuntuforums.org/showthread.php?t=1340466](http://ubuntuforums.org/showthread.php?t=1340466)

supposedly it didn't work for another user with a Via P4M800 but maybe it will for you.

---

