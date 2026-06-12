---
title: "Display issues when remoting from Windows via xRDP"
date: 2014-03-19
forum: Networking &amp; Wireless
---

### Post by max36 on 2014-03-19
Hey all,

I am having a strange issue when remoting from Windows to Ubuntu using xRDP. I can initialise the connection fine and enter credentials, however the desktop appears like this with a black 'X' cursor: 

[IMG]http://i.imgur.com/SCXmsAM.png[/IMG]

Is there some package that needs to be installed on Ubuntu to allow full graphical access?

Thanks,

---

### Post by TheFu on 2014-03-20
That is probably the root X/Windows window.  That is what it looks like to me.  

Right click on the mouse to see a menu.  If you want some specific DE (desktop environment) or some specific WM (Window Manager), then run it.  Does that make sense?  Try running **/usr/bin/openbox &** to get a minimal WM setup, suitable for remote desktops.

If you _need_ a DE, LXDE is nice - install it with **sudo aptitude install lxde** and run it with
**/usr/bin/startlxde &**

I haven't tried this - but ALT-F2 might pop open a program launcher to call these things.  I always get an xterm console (without WM) in my remote sessions by calling **/usr/bin/xterm &**. Then I can decide which WM or DE  will be run.

---

### Post by WB0HYQ on 2014-05-02
I get exactly the same thing.  No mouse clicks are possible.  Nothing reacts to the keyboard.  Just the grey screen.  Ubuntu 12.04LTS 64-bit

Bill

---

### Post by TheFu on 2014-05-02
> **wb0hyq said:**
> i get exactly the same thing.  No mouse clicks are possible.  Nothing reacts to the keyboard.  Just the grey screen.  Ubuntu 12.04lts 64-bit

bill

alt-f2?

---

### Post by WB0HYQ on 2014-05-02
Um, "nothing reacts to the keyboard".  I.E. keypresses don't register (do anything).  I have beat myself silly for two days trying to get this running so I can control my downstairs Ubuntu server from my Win7 computers upstairs.  Makes life a whole let better if I don't have to keep running downstairs just to do something.

Bill

---

### Post by WB0HYQ on 2014-05-02
Here is what I am seeing now after restarting the Ubuntu machine.

Bill

---

### Post by TheFu on 2014-05-02
Until you get the GUI stuff working, putty and ssh can work.

Sorry, I don't use rdp for Linux connections. NX is what I use. It is a little more involved to get working, but it is 2-3x more network efficient AND secure. No good Android client exists for NX, but the Linux and Windows clients are very good.

Or you could use pure X/Windows. That can work if on the same LAN, but never good for use over the internet - bad security.

---

