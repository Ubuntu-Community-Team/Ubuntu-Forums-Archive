---
title: "Ubuntu 8.10/ Gnome freezing up"
date: 2009-04-10
forum: New to Ubuntu
---

### Post by ericstrom on 2009-04-10
Very new to ubuntu so please be patient with me. I've been running 8.10 for a few weeks and no problems until recently. Suddenly I'm having probleems with my system feezing up shortly after I'm on-line for maybe 10 to 15 minutes. What happens is the I lose the color on the screen and everything goes black and white. Shortly after that the entire PC locks up and won't respond to ANY mouse clicks. I can exit the web site. I can hit system shutdown. The only thing I can do is push the power button and do a hard reboot. 

I suspect the problem happens when I'm on a website that uses a lot of resources such as aol.com and I'm using Pidgen at the same time. 

I have no idea what to do. Any suggestions would be GREATLY appreciated.

---

### Post by mp035 on 2009-04-10
First of all, try disabling your screen saver, I had a similar problem once like that.  It was the screen saver not letting me back in.

Second, next time it happens, hit Ctrl-Alt-F1, this should give you a console screen with a login prompt.  Hit Ctr-Alt-F7 to return to the graphical terminal.  If those two key combinations work, then try Ctrl-Alt-Backspace to restart your X server.  All your running programs will exit, but at least you won't have to reboot.

If the above key combinations don't work it could be hardware related. :(

---

