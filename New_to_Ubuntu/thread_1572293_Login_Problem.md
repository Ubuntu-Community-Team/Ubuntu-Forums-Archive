---
title: "Login Problem"
date: 2010-09-10
forum: New to Ubuntu
---

### Post by unh4nd13d on 2010-09-10
so, I partitioned my hard drive using wubi and am ruining ubuntu 10.04 on my Acer Aspire 5536 laptop. 
I haven't been having any problems with ubuntu but today I tried to login, the login screen came up like usual, I put in my password and hit enter like usual. This time instead of everything loading like normal, the back ground for the login page stayed and nothing loaded only a terminal window in the upper left hand corner. I've tried the "gnome-session" to no avail. I could really use some help with this. Thanks

---

### Post by Chevex on 2010-09-11
Awwww how cute, you adopted my username. I feel so admired.

---

### Post by Silent Warrior on 2010-09-11
I don't know much about that... but my experience with ArchLinux and the ardours of installing X on it tells me you're starting an 'xterm'-session. Why you get that instead of Gnome is anyone's guess, though. But if you get good graphical output, all's not lost.
I even think you have a few options.

1. Install a different display-manager (kdm, lxdm, slim, xdm, whatever, as long as you configure it to be used) and reboot, hoping it will let you back in.
2. Check for any broken packages [sudo apt-get -f install]. Reinstall gnome-session if you believe it necessary.
3. ... Hm... No, can't think of anything more. Any further suggestions?

---

