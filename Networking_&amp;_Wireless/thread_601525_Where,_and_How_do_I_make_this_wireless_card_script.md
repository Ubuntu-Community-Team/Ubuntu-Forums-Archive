---
title: "Where, and How do I make this wireless card script?"
date: 2007-11-03
forum: Networking &amp; Wireless
---

### Post by Amazing_Ri on 2007-11-03
Hello all.  I've been toying with Ubuntu since 6.04 and really like it.  But there is one thing I still can't figure out.  I have an old Dell 2200 laptop with a Broadcom card, and I managed to get it to work using several turorials here and around the web. 
 However, one of the steps to overcome the dreaded "Stuck at 28%" ghost is the following command at terminal
  sudo iwconfig ethX essid x mode managed
This works like a charm so far, but since I am not the primary user of this machine, I would like to write a script to automagically run this command after a user logs in.  Can this be done, or should I run it at startup instead?  And really, how do I do either?  
I know I can't offer much beyond my thanks and respect, but if anyone can help me figure this out, they will have both...:KS

---

### Post by soluphobe on 2007-11-03
I had to do something similar when I got my wireless working.  One way to handle it *might* be (I'm not sure, and you should probably back up your system and stuff) to add your command to a file called 99-custom.rules in etc/networking/udev , which I think runs every time the computer starts up.

The way I understand it is that everything in udev is run when the computer boots on (not sure which), and it runs the files in order.  naming you file 99-whatever.rules will make sure it is run last, and it will run that command for you every time the computer boots.

---

### Post by Amazing_Ri on 2007-11-04
I thought about something similar, but is there a difference if it runs at at start up, or at log on?  And does it have to be named that exact file name, because I read somewhere about an existing file with auto-run commands somewhere in /.user.  Is that the one I should use?

---

### Post by kevdog on 2007-11-04
If you put those commands associated with user login, they will only be available when the user logs in.  If you have other users to the system this may cause a problem.

Most people want the wireless interface activated when the systems starts (however this may not be what you want).

---

### Post by Amazing_Ri on 2007-11-04
I'm okay with it starting when anyone uses it.  I just wanted to make sure it could work on startup, and that it did not need done with each log in.  So since I'm really new to this whole script making thing, can someone explain how to do it.  I would love to learn the hows and whys, but if no one has the time or patience for it, a simple copy/past and where to put it would be awsome as well.  But I'd really enjoy a lesson on the hows and whys of scripting too...

---

