---
title: "WoW Lowerping / Battleping / Smoothping in Ubuntu?"
date: 2010-08-19
forum: New to Ubuntu
---

### Post by Bosk on 2010-08-19
G'day guys,

I'm a long time WoW windows xp player and have recently made the switch to Ubuntu. I normally use one of the three WoW tunnelling services listed in the topic title to lower my WoW ping from the 400's to the 200's. (I'm in Australia which is why pings are so high)

Although I've managed to get WoW up and running in Ubuntu just fine (no hardware cursor yet but I'm working on it) I have so far had zero luck getting any of these tunneling programs to work under Wine. Well, actually that's not entirely true - Smoothping does work (it uses Freecap & Putty) but when logging into WoW after following all the Smoothping instructions WoW just sits there at the login screen and does nothing.

Although my "native" ping is almost 100ms lower in Ubuntu than it was in XP (a welcome improvement) it is still higher in Ubuntu than it was on XP using a tunneling service. 
I'm hoping that by getting some sort of tunneling service to work in Ubuntu I can lower my ping still further.


Would anyone have any suggestions as to how I can resolve this situation please? 
Many thanks for your time.

---

### Post by Bosk on 2010-08-19
Bumping the thread because I'm really hopeful someone will be able to help me out.

I don't necessarily need to get any of the 3 tunneling services I listed to work, I'd be just as happy to find another similar service that works in Ubuntu.

Cheers guys.

---

### Post by NCLI on 2010-08-19
I think you'd be better off using one of the many ways [Wine itself provides support]("http://www.winehq.org/help/").

---

### Post by cokeijo on 2011-10-05
For those who wants to run WoW on Linux with LowerPing, install Sockscap INSIDE WINE as shown in the following thread:
[http://www.lowerping.com/forums/showthread.php?3944-Sockscap](http://www.lowerping.com/forums/showthread.php?3944-Sockscap)

Add WoW to Sockscap list as if you were inside windows.

Install PuttY  INSIDE WINE as shown in the following thread:
[http://www.lowerping.com/forums/showthread.php?3941-Putty-List-tips-and-tricks](http://www.lowerping.com/forums/showthread.php?3941-Putty-List-tips-and-tricks)

To add the servers type on a terminal:
wine regedit "PuttyServersRegFile" where  "PuttyServersRegFile" is the path to the registry file containing the servers provided by LP.

Run PuttY and connect to your preferred server. Run WoW clicking on Sockscap apps list.

These two programs are not lowering WoW FPS and my ping is good.

---

### Post by sffvba[e0rt on 2011-10-05
Back to sleep thread...


404

---

