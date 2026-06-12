---
title: "Screen Resolution Goes Out of Range"
date: 2008-12-27
forum: New to Ubuntu
---

### Post by ScotWithOneT on 2008-12-27
My screen resolution goes out of range(blank display) prior to the Login 

Screen.  Video output is working and displayed on both monitors during the 

POST, Kernel Load and Ubuntu Progress Bar.  I use Ubuntu 8.04 64 bit and a 

Nvidia 7800GT graphics card.  Any help in this matter is greatly 

appreciated.

---

### Post by RomeReactor on 2008-12-27
Hi. It seems you're using a dual display. Have you tried booting with only one monitor connected? Or have you tried booting into recovery mode?

---

### Post by ScotWithOneT on 2008-12-29
Thank you.  I disconnected the 2nd monitor , booted into Recovery Menu, ran XFIX to try to fix the XServer then 

resumed normal boot.  There is a normal Login Screen that after entering the particulars my screen becomes orange with 

a white rectangle in the upper left quadrant of the screen(LCD 1366x768).  It seems like the system is frozen,but 

after waiting I come to the normal desktop but with an Error Message:'There was an error starting the Gnome settings 

Daemon. Some things such as themes,sounds,or background settings may not work correctly.  The last error message 

was: Did not receive a reply.  Possible causes include the remote application did not send a reply, the message bus 

security policy blocked the reply, the reply timeout expired, or the network connection was broken.  Gnome will try 

to restart the settings Daemon next time you log in."  I was able to repeat the previous login attempt exactly minus 

the Error Message.  This is a good starting point to resolve my resolution issues.  I believe my main problem is 

proprietary Video Card issues(Nvidia GeForce 7800GT).

---

