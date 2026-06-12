---
title: "LAN help..."
date: 2005-11-23
forum: Networking &amp; Wireless
---

### Post by DiscoKiller on 2005-11-23
hey all, i`ve somehow managed to brutally sodomise my ubuntu installation and as a result need to reinstall the xserver thingymabob...i`m new to all this....was wondering how it would be possibe to log in to my LAN server (uni residential network) to gain access to the net from a terminal command. problem i have is that i cant load up the GUI so i`m left with terminal (my worst enemy [yeah yeah i`m still not used to being away from windows]) to sort out the problem as i dont want to have to go through yet another full reload.

---

### Post by DiscoKiller on 2005-11-23
thought i`d mention i`m trying to do the apt-get install xserver-xorg command but it is telling me the package is not found, i can only assume this is because there is no connection present to the repositories...i.e. internet connection which i must do through a proxy.

---

### Post by wrtrdood on 2005-11-23
X may actually be OK but the display manager isn't running for some reason.  You can check this with the **startx** command.  If that doesn't work then, yes, you get to become friendly with the command line.

A quick check for network connectivity can be performed using the **ping** command at the command line.  I ususally ping a site like this:

    ping [www.tux.org](www.tux.org)

(ctrl C to exit)

If you get returns, you're talking to the internet.  If not, check that you can ping one of the IP addresses on your LAN to be sure you're even getting outside this machine.  If that's also a negative, check your local config with the **ifconfig** command and be sure the systems's NIC has an address defined.  If this is all good, you need to verify the routing, checking first for a defined gateway.

---

### Post by DiscoKiller on 2005-11-23
ok total newbie here btw. i know for a fact im not commuicating with the internet. the way my connection works is that i open the browser which goes straight to a site to log in to my residential network, the problem i have is i need to get my login details to said proxy without the nice gui to help me along the way. as for the startx command i get a series of thingies telling me stuff, i shall copy it down as best as i can though i`m using two seperate machines so i have to handwrite the error message....

after typig startx...

skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_clip.o" No symbols found
skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_norm.o" No Symbols found
skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_xform.o" No Symbols found

then some stuff telling me where to find the log file and to go to somesite for help...then it says

Fatal Server Error:
no screens found

X10: fatal IO error 104....


anything useful there?

---

