---
title: "What exactly is an X server?"
date: 2010-06-07
forum: New to Ubuntu
---

### Post by IAmAnarch on 2010-06-07
I've heard about X/X11 a lot, but what exactly is it (in beginner's terms, a comparison to Windows would be nice).

---

### Post by Possum Films on 2010-06-07
> 
(copied from [http://toastytech.com/guis/x.html](http://toastytech.com/guis/x.html))

Linux, and other Unixes don't require a GUI and can often be run just fine from a command-line interface. They do, however, have a graphical system known as the X Windowing System or simply "X" 

The **X-server** program is the program responsible for taking  drawing requests from programs on the local or remote computer, talking to the video display, and returning information to the program from the mouse or keyboard. 
Additionally, the X-server requires a separate program called the  **window manager** that handles window controls such as the title bar, minimize or maximize buttons, controlling the resizing and moving of windows, and providing methods of launching applications. 


So basicly the X server is the program that is used to draw windows on the screen and interact with the mouse and keyboard. 

On Ubuntu the X Server is called X.Org

---

### Post by Drenriza on 2010-06-07
The xorg service is responsiable for drawing windows around programs & applications. Also it can send information to an windows manager for example Gnome or KDE to get it to look better.

Also the xorg service can be used to have remote multiple users on a server. The users can then log in to this server and get their personialised user desktop, on the computer their at.

---

