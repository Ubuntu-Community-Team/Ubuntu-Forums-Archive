---
title: "lost top menu bar"
date: 2009-06-16
forum: New to Ubuntu
---

### Post by rburkartjo on 2009-06-16
the bar i am refering to is the one that when you open the home folder says

file edit view go bookmarks tabs help

i know it is somethng i have done to my desktop because it still appears on my duaghters. any ideas how to get back

---

### Post by SOULRiDER on 2009-06-16
AFAIK you cant do this on GNOME, try pressing alt and releasing it and see if it appears.

If youre using KDE theres a key binding to hide/show the menubar, i cant remember what it was, but i think its something like alt + M

---

### Post by QIII on 2009-06-17
Please read my whole post before you do anything.  Especially the "disclaimer" at the bottom!

I found this:

[http://www.watchingthenet.com/restore-panels-in-ubuntu-back-to-their-default-settings.html](http://www.watchingthenet.com/restore-panels-in-ubuntu-back-to-their-default-settings.html)

This apparently worked in 7.10 and 8.04.  I haven't found anything definitive for Jaunty.

Take care to read it first.  There is a correction:  Don't use "gconftool-2 --shutdown", use "gconftool --recursive-unset /apps/panel"

The commands in the article have to be run in the terminal, which you probably can't get to using the buttons on the panel that you can't see.

You can start the X terminal by pressing Alt+f2 and typing "xterm" (without the quotes) in the box with the blinking cursor and pressing enter.

"Friendly, helpful disclaimer:"

1.  Before you do this, wait a while for someone else to look it over.  It is always a good idea to have someone else confirm what you are doing when someone on the forum says "run this or that command."  The monitors are usually right on top of people who suggest malicious commands, but you still need to be careful.  You don't know me from Adam.

2.  Someone else may know if this will work in Jaunty or not.  If someone says this is not a good idea in Jaunty, don't do it.  Unfortunately, I upgraded my "dev" copy of Jaunty to test Karmic, or I would have run through this before even posting it.  

3.  If you don't get a response in the next 24 hours, you may want to bump the thread.  But I think you know the deal:  DO NOT DO THIS in any less than 24 hours.  It is considered discourteous to do so, it is against forum policy and the monitors will let you know that.

---

### Post by nothingspecial on 2009-06-17
If you are using compiz fusion it is possible the window decoration plugin has been turned off.

Go into compiz settings manager and turn it back on.

I happen to like my windows that way.

---

### Post by rburkartjo on 2009-06-19
tks everyone for your help. nothing didnt check it out before i fixed it another way but i think what you said caused the menu to disappear will remember that next time

---

