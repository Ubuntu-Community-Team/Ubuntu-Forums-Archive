---
title: "Wireless Connection Loss Results in Gutsy Crash"
date: 2007-12-23
forum: Networking &amp; Wireless
---

### Post by bakketti on 2007-12-23
This is a weird problem. I am running Gutsy on a Dell 1420 (using ipw3945 wireless driver). Never have had wireless problems at home and many other places. However, I am at my parents home for the holidays where they are running a Microsoft MN-500 wireless router. 

Long story short, Gutsy connects just fine to the network and I use the Internet for awhile. At some point, I loose the connection. Ok, thats fine. Its a Microsoft router... maybe it sucks. However, when the connection is lost, the nm-applet seems to crash. I try to re-connect and I have no luck. On top of this, the rest of Gnome seems to give up. I can no longer open any other programs unless they have already been open. For example, I had the terminal up after a connection loss and I can type in the terminal and run simple programs like "ps" and "kill". However, running "iwconfig" just hangs up in the prompt.  Next, I do a Ctrl-Alt-Bkspc to restart  Gnome. No luck, it gets stuck on trying to run /etc/rc.local. This script only has "exit 0" in it. 

I eventually restart my computer, reconnect to the network and do this process all over again. This has happened about 4 times today so far. I am only going to be at my parents house until the 26th so its not a huge deal, but this problem has completely baffled me. I dont have a clue!

Any ideas or suggestions? So far, my only idea is to get them a new router for Christmas. :)

---

### Post by l0stendeavor on 2007-12-29
I'm bumping this because I'm having this same problem but on multiple routers so it must be an internal problem. The crash is forcing me to hard reboot my machine which gives me concern to possible data loss and hd problems. Any suggestions would be greatly appreciated.

---

