---
title: "Secure Remote Connection"
date: 2009-02-20
forum: New to Ubuntu
---

### Post by omni504 on 2009-02-20
Ok, so i've still been exploring my ubuntu system (its beautiful after the first couple weeks of headache you go through trying to get through your head that it is NOT windows, heh), and everytime i see a new application or feature that seems interesting, I just google some HOWTO's (most of which lead right back to this forum) and check it out. But there was one feature that i wanted to get to the bottom of and still havent.

The "Secure Remote Connection" option on the login screen (after you click on "session", before logging in) for your ubuntu. I've fiddled around with, and successfully connected to a windows laptop, through ssh/vnc, but that requires you to be connected to the internet. You're not connected if you're just logging in.

So i was wondering what is that "session" used for exactly?

---

### Post by taseedorf on 2009-02-20
It allows you to have secure connections with the X server and log into a network.....

---

### Post by omni504 on 2009-02-21
Does anyone know some "HOWTO"s or anything that would help me understand it more? From what i can tell it's not really like vnc or ssh right? I aready fiddled around with those and it involves getting both server and workstation ready, this doesnt seem like that. And im a really curious person, especially when i see something interesting like that.

So ya, anybody know where i can get more info (i would've asked somebody on the forum to answer it, but id like t completely satisfy my curiousity and i don't think anybody would be willing to type up a essay for me ;) ).

---

### Post by m3wolf on 2009-03-25
If you use this option it basically lets you log in to another computer as if it were the one you are on.  It is similar to the XDMCP way of doing things except that it goes through an SSH connection and uses TCP/IP instead of UDP.  I'm still working on getting mine set up so I'm not sure exactly what you need to have installed on the server machine.

If anyone reading this has any more info: when I log into my remote desktop this way every icon, menu, even my desktop image are all upside down.  They are in the right place, just upside down.

---

