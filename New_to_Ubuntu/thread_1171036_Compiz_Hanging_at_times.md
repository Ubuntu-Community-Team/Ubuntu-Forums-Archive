---
title: "Compiz Hanging at times"
date: 2009-05-26
forum: New to Ubuntu
---

### Post by raziiq on 2009-05-26
Hi there.
i have installed compiz config Manger and using it for some of the cool graphics stuff like, rotate cube, Desktop cube, expo, burn etc.

Sometimes when i use Expo(Super+e) computer hangs or i must say desktop hangs(as songs in the RhythmBox play without interruption even if desktop hangs). Similary computer sometimes hangs when i use Rotate Cube(Clt+Alt+Mouse).

Is there any way of getting rid of this?

Will using clt+alt+F1 work?

---

### Post by TheNosh on 2009-05-27
if you're running jaunty with intel graphics, chances are it has to do with blacklisted drivers needed to run compiz. did you manually install blacklisted drivers after you upgraded to jaunty? (are you using jaunty?)

if this is the case, the solution is to not use desktop effects, go back to intrepid, or accept the occasional system hang

if theres another way of dealing with this i don't know it. maybe someone else can shed more light

---

### Post by raziiq on 2009-05-27
ya i m on Jaunty and i m using Intel graphics as shown in my Signature too. Alright i can understand that i have to compromise a bit, thats ok with me, but what if desktop hangs?? Should i restart the PC or is there any other way to restart the desktop like we have Task manager in Windows, where we can end task the Explorer and then restart it again?

---

### Post by QIII on 2009-05-27
Do the applications you are using "go gray", or is there no change in appearance of your desktop except that you can't do anything?

---

### Post by raziiq on 2009-05-27
BTW what is Desktop in UBuntu called, like we call it Explorer in Windows?

---

### Post by TheNosh on 2009-05-27
the explorer equivalent is Nautilus

---

### Post by raziiq on 2009-05-27
means if my desktop hangs , i can kill the Nautilus and then start the Nautilus again to get it to the normal??

---

### Post by TheNosh on 2009-05-28
no, windows habbits don't translate directly into linux, your best bet would be to restart X, which would also close all your apps (but based on your description of your situation, even that won't work, so you would need to reset the computer)

dropping out of X used to be [ctrl]+[alt]+[backspace] till it was disabled in jaunty, but it can be re-enabled 
[http://www.ubuntugeek.com/howto-enable-ctrl-alt-backspace-in-ubuntu-jaunty.html](http://www.ubuntugeek.com/howto-enable-ctrl-alt-backspace-in-ubuntu-jaunty.html)

but as i said that may not even work in your situation, so i would advise turning off compiz when doing anything important, turning it off all together, or going back to intrepid.

---

### Post by raziiq on 2009-05-28
that CLT+ALT+backspace is also a good one to use at times, thanks for that

---

### Post by TheNosh on 2009-05-28
agreed, i was upset when they disabled it, till i found out how to get it back. apparently they thought it would be pressed by windows users thinking it was like [ctrl] + [alt] + [del] and then they would get frustrated when it closed all their apps

---

