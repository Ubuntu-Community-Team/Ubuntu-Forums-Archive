---
title: "Help installing Wally wallpaper changer"
date: 2010-04-14
forum: New to Ubuntu
---

### Post by munnster on 2010-04-14
This is not my first attempt at getting Wally working.  Having used John's Background Switcher in Windows, I want to get this working in Ubuntu.  I managed to download (through terminal) libqt4-dev, qt4-qmake, and qt4-dev-tools and then navigated to my download of the .deb package and typed 
sudo dpkg -i wally_2.3.2-1_i386.debafter asking for my password, this is what I got:

Selecting previously deselected package wally.
(Reading database ... 130361 files and directories currently installed.)
Unpacking wally (from wally_2.3.2-1_i386.deb) ...
Setting up wally (2.3.2-1) ...

Processing triggers for desktop-file-utils ...
leanne@ubuntu:~/Desktop$

Did I miss a step?  Whenever I open Wally, it shows the splash screen for the program, but I cannot access any of the controls at all.  Left click tells me wally is already running and right click only give me "launch, properties, remove from panel" etc.

Any help is greatly appreciated. :D

---

### Post by jloveless on 2011-02-22
I realize this question was just short of 1 year ago, but I may have  solution if you haven't already figured it out. Right click the panel and select "Add to Panel...". Look for "Notification Area". Select this and it will put a vertical bar near the right edge of your panel. The actual Wally icon should now be the first icon (a small square). Right click on this icon and select "Settings". You will probably see a couple of additional icons also, like speaker volume and network - all depends on your setup. I am using it with x64 and Ubuntu 10.10.

Jon

---

