---
title: "Keyboard and Mouse problems"
date: 2010-11-16
forum: New to Ubuntu
---

### Post by deanom on 2010-11-16
Hi
Just tried running Ubuntu from CD, and then as a dual boot. 
From CD whole screen froze. No response from mouse or keyboard.
From Dual Boot, could not use down arrows to select boot from Ubuntu.
Both mouse and keyboard are USB, and have windows drivers.
Am running XP SP2, mouse is Razer krait, keyboard is Saitek gaming. Computer is self built.

---

### Post by deanom on 2010-11-16
Will have to come back to this tomorrow, to see if there's a solution.

Deano

---

### Post by chamira on 2010-11-17
You need to plug in the Keyboard to a PS/2 slot - you might have got a small plastic adapter with your USB keyboard & mouse that allows them to be plugged in to those slots. 

I think the USB drivers load up during the operating system boot up, not at the bios stage which is where grub and dual boot menus appear.

As to why it froze during Live CD install - there is a lot of data to read and it does take a sometime. Have eyou tried to run Ubuntu throught the Live CD first just to verify that it is all working?

---

### Post by deanom on 2010-11-17
Hi Chamira
I tried the Live CD first. Ubuntu booted up all the way through to the desktop. I got mouse movement until I clicked on Firefox, and then everything froze. I had to switch everything on and off. Second time around I got no cursor movement when using the mouse.
I then installed to allow a dual boot, but cannot select Ubuntu. No movement using arrow keys, arrow keys on numeric keypad, or using the TAB key.
I'll have to check the boxes in the attic to see if there is a PS/2 adaptor for either the keyboard or mouse. Both are plugged into separate USB ports currently.
I'm going to try uninstalling, and then running from the Live CD again. Then look for an adaptor if that doesn't work. I've sort of resigned myself to having to buy a cheap PS/2 keyboard and mouse if I can find one.

Thanks for the reply, and I'll keep you posted.

Deano

---

### Post by deanom on 2010-11-17
I tried the LiveCD again. It showed a cursor, which moved with the mouse, but did not allow me to open anything.
I then tried a copy of 10.4, which came with a book, and that seemed to function OK, except that for some reason Internet access was too slow, and I kept on getting timed out. it did get to the Ubuntu start page, but I couldn't access anything else. 
it seems that it is the CD that is at fault with 10.10, but before I proceed to try an install of 10.04 is there anything that I need to do to speed up internet access, or is that down to working from the LiveCD?
If the question should be part of a new thread, could a moderator do that for me, or do I just start a new post?

Thanks

Deano

---

### Post by LowSky on 2010-11-17
you shouldn't need a PS/2 adapter. all newer computers will run on USB at boot. I haven't needed one in years.

LiveCd should just work with no glitches except for being a bit slow, you're running off a CD its not exactly the fastest option.

I'm not sure if you installed using Wubi or a normal LiveCD method as installing Ubuntu using the LiveCd will cause the system to boot directly to Ubuntu unless you choose otherwise.

Another thing to note is using Microsofts built in IOS burner is not exactly great at making ISO the way they are supposed to.

Check out this [http://isorecorder.alexfeinman.com/isorecorder.htm](http://isorecorder.alexfeinman.com/isorecorder.htm)

---

### Post by deanom on 2010-11-17
Hi LowSky
Thanks for the reply.
I've just tried a Wubi installation, and still am not able to select Ubuntu at boot. Windows is highligted, and I am unable to change that. This CD is 10.04, and worked ok directly from the CD, other than extremely slow internet, leading to timeout messages. I would try installing direct from the CD, but if I experience the same problems (unable to select windows, and slow internet access) I'm stuck.
What I need is a way to select at boot. I still do not know if it is a hardware problem, or a software problem, or how to fix it.
Determined to get it to work, but without the knowhow.

Deano

---

### Post by walt.smith1960 on 2010-11-17
I just had something similar happen. I've had a USB keyboard and Kensington Orbit trackball installed on a 2004-2005 vintage M.B. Both worked fine in both Ubuntu and some Linux-based bootmanager & backup software.  I just installed a new Gigabyte M.B. and the USB trackball doesn't want to work with the non-Ubuntu software.  The keyboard won't work unless legacy USB is enabled in BIOS. I'm lucky to have an old PS2 trackball which works fine on the new M.B. and all programs so far. This new M.B. has one PS2 port so I guess if the keyboard didn't work I'd need to get a PS2 Y cable.  It could be a hardware problem or a hardware/software conflict.  I'd have thought by now that USB would be universally functional especially on new hardware but I guess not.

---

### Post by deanom on 2010-11-17
:confused:Hi Walt and others
This is getting frustrating. The keyboard and mouse work fine on the livecd, using 10.04, but internet access is almost non existent, as the connection is too slow, and is timed out. 
Trying through Wubi, I am unable to select Ubuntu to boot. Trying an install from the Livecd ended in a crash.
This is the second evening spent trying to see if Ubuntu will do what I want it to, and at the moment, the answer is no, which is a shame, because if I cannot get it to function, I'll have to stick with what I've got.
Two issues to resolve. Getting a decent internet connection working through the Livecd, so that I'm confident enough to go for a dual boot install. Then being able to select the right OS at boot.
Still in need of help

Deano

---

