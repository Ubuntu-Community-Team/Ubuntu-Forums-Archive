---
title: "Problem logging in to Xfce session"
date: 2010-01-24
forum: New to Ubuntu
---

### Post by auburnfan2015 on 2010-01-24
I did a fresh install of Ubuntu Karmic on my Dell Mini 9, got it up and running, and installed Xubuntu through "sudo apt-get install xubuntu-desktop".  I rebooted, logged into Xubuntu, and everything ran smoothly. When I left the room, I powered down my Mini 9 properly and plugged it in to charge. Just now, I tried several times to log into an Xfce session like normal, but when I put in my password, my Xubuntu background and a cursor appears and nothing else. I can't do anything with the cursor but move it, but I can open terminal with ctrl-alt-F1.  I powered down and logged into a GNOME session, and it worked perfectly. Ubuntu's up and running with no problems. Can anyone explain why the Xubuntu environment is not loading?  

Thanks in advance for the help!

---

### Post by 4Orbs on 2010-01-24
My guess (yes, guess) is that the Volume Control applet that is default on the xfce desktop is not finding Alsa audio (because Ubuntu uses pulse audio) and as a result is preventing the xfce panels from loading. Hopefully someone will post an easy solution to your problem soon.

---

### Post by auburnfan2015 on 2010-01-25
Thanks for the help, but I wasn't able to find anything online relating my failed DE and the alsa drivers.  

Bump for some more help

---

