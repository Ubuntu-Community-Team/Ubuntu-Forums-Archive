---
title: "Hardy Heron: frequently hangs using wireless"
date: 2008-05-31
forum: Networking &amp; Wireless
---

### Post by sunogbahay on 2008-05-31
I recently upgraded to Hardy Heron. Everything works really well in the upgrade except for a small problem.    When I am using a wired internet connection.  The system is very stable.  I can work all day without any problems.   However, when I connect via wireless, I can only work 20min to an hour before my machine just hangs.   I can't kill X or <ctrl>+<alt>+<del> or switch to any other tty terminals.   I have to kill the machine by forcing a power-down.  

This is a new feature ever since I upgraded.  I am kind of stumped on where to start debugging.  I have tried looking at the system logs directly after a crash but I don't see anything obvious.

The machine is an older Dell C400 Latitude.

Any ideas on what might be going on or where to start looking?

---

### Post by sunogbahay on 2008-06-10
Just an update to my previous post.  
I followed the instructions here:[_WirelessTroubleShootingGuide_]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide") 
about disabling ipv6 and this seems to have solved the hanging problem.

---

