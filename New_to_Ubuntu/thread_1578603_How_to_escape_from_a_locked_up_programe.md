---
title: "How to escape from a locked up programe"
date: 2010-09-20
forum: New to Ubuntu
---

### Post by wheels666 on 2010-09-20
Hi - i'm using Ubuntu 10.04 on a dual boot with win XP

on a couple of occasions i've had the computer lock up in firefox and nothing would work - in windows i would press cnt/alt/del and end firefox

pulling the plug out of the computer is my current fix, but it's a bit crude

Does Ubuntu have a ctrl alt delete equivalent?

:-k

---

### Post by coffeecat on 2010-09-20
You can force quit a misbehaving app. Right-click on the upper panel, select "add to panel", highlight the "Force Quit" applet and then click on Add. The next time you have a frozen app, click on the force quit applet icon, move the mouse cursor to the frozen app, click again and follow the prompts.

If the whole computer is frozen solid, you need the magic key sequence. Hold the Print and Alt keys down (on some machines it has to be the Alt Gr key instead of the Alt) and then press this sequence of keys (not too quickly): R E I S U B.

More here:

[http://en.wikipedia.org/wiki/Magic_keys](http://en.wikipedia.org/wiki/Magic_keys)

'B' didn't work on one of my machines, so if you get that use O instead for a shutdown: R E I S U O.

---

### Post by MartyBuntu on 2010-09-20
System > Administration > System Monitor > *click the "Processes" tab *

...choose the application that froze up, right-click, "Kill Process".

---

### Post by jtarin on 2010-09-20
If you only have a locked app....you can enter the command [COLOR="Red"]xkill[/COLOR] in a terminal and use your mouse to close it.

---

### Post by Dustin2128 on 2010-09-20
there's also the option of renabling ctrl-alt-backspace, which was for whatever reason disabled by default since jaunty. It kills everything and brings you back to the login screen.
[http://www.ubuntugeek.com/enable-ctrl-alt-backspace-in-ubuntukubuntu-10-04lucid-lynx.html](http://www.ubuntugeek.com/enable-ctrl-alt-backspace-in-ubuntukubuntu-10-04lucid-lynx.html)

---

### Post by wheels666 on 2010-09-20
many thanks for these suggestions - i will try them all out - just waiting for the next lock up!
this thing of people helping out by answering questions is brilliant and much appreciated

---

### Post by Cathhsmom on 2010-09-20
You can also add force quit to your panel.

---

### Post by jtarin on 2010-09-20
> **wheels666 said:**
> many thanks for these suggestions - i will try them all out - just waiting for the next lock up!
this thing of people helping out by answering questions is brilliant and much appreciated
This not exclusively Ubuntu Forums....there are many Linux related forums past and present that have done this for years....its a movement, man.:P

---

### Post by garyed on 2010-09-20
You can also do:  Alt F2  then type the command xkill in the box.
Then click on the window that is locked up.

---

