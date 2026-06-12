---
title: "New to Linux mouse not clicking???"
date: 2011-06-18
forum: New to Ubuntu
---

### Post by Squ1rr7y on 2011-06-18
I just installed ubunto 11.4 gnome 2.32.1 
64bit, on my dualcore @2.13Ghz 4gb ram

I would call my self a advanced user of windows. reason why I chose this version of Linux. I have split my 1tb hardrive in half. One side win 7, the other ubunto. I can't figure this thing out. For one my mouse moves around I can click the "z" button on the bottom but mouse clicks don't work for anything else???
I have a cyborg rat 7 gaming mouse.  Do I need drivers before this thing will actually work or what?

---

### Post by amauk on 2011-06-18
Seems to be a known issue

From comment #23 here
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/615892](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/615892)

> Steps to get RAT 7 working:

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

---

### Post by conbot on 2011-06-18
Try a different mouse? Is it USB or PS/2? #-o

---

### Post by Squ1rr7y on 2011-06-18
I tried doing what you said I entered in the info into the xorg.conf but when I hit save it would not work. 
This OS Is retarded the <snip> mouse won't work. <snip> Linux .....format

---

### Post by nzjethro on 2011-06-18
> **Squ1rr7y said:**
> I tried doing what you said I entered in the info into the xorg.conf but when I hit save it would not work. 
This OS Is retarded the <snip> mouse won't work. <snip> Linux .....format

What do you mean it would not save? Did it give any error message, or any reason why it would not save?

---

### Post by jtarin on 2011-06-18
> **Squ1rr7y said:**
> I tried doing what you said I entered in the info into the xorg.conf but when I hit save it would not work.You must do it as root. If you typed sudo it should have worked , but you failed to report any errors.
> **Squ1rr7y said:**
> This OS Is retarded the <snip> mouse won't work. <snip> Linux .....formatThere is no such thing as a retarded OS. It's an impossibility. Possibly operator error, hardware failure or software bug, as a totality....no.:P

---

### Post by LowSky on 2011-06-18
TROLL... it looks like he is already gone.

---

