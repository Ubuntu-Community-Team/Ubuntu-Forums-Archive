---
title: "Pidgin is freezing on startup after using internet at a hotel"
date: 2008-03-23
forum: Networking &amp; Wireless
---

### Post by rainwalker on 2008-03-23
I connected to a hotel's network both wirelessly and with an ethernet cable on a trip to Houston, and upon returning home I connect successfully with my home network and everything works fine except Pidgin. As soon as I start it, the window from NickServ that should tell me to authenticate my nick pops up and Pidgin freezes. When I try to close the window, it says the application isn't responding and I have to force quit.
Running Pidgin from a terminal, I get this:> sh: jackd: not found
sh: jackd: not found
DCOPClient::attachInternal. Attach failed Could not open network socket
DCOPClient::attachInternal. Attach failed Could not open network socket
ERROR: Couldn't attach to DCOP server!
I used Pidgin while at the hotel, and everything worked fine. Any ideas?

---

### Post by rainwalker on 2008-03-23
Okay, so I found a post on another forum talking about the musictracker plugin, which I installed a while back. So, I started Amarok and ran Pidgin again, and it works fine. From the terminal, the only error I get now is the> sh: jackd: not found
sh: jackd: not found part.
I've been using musictracker for a couple of months with no problem, whether Amarok was running or not.

---

### Post by rainwalker on 2008-03-23
Ok, now for some reason Pidgin starts fine without Amarok...
If anyone still has any info on why the musictracker plugin messed this up, please share

---

