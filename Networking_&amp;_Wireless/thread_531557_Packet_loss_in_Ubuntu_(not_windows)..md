---
title: "Packet loss in Ubuntu (not windows)."
date: 2007-08-21
forum: Networking &amp; Wireless
---

### Post by Jungleboss on 2007-08-21
I'm getting ~3-5% packet loss when pinging my dlink router (DGL-4300) from Ubuntu. The wierd thing is that from windows I don't get any packet loss! I have a wired connection with both computers (no wireless). Surfing the web doesn't work at all or is very slow.

Also losing my dhcp ip address sometimes in Ubuntu (getting 169.x.x.x address in that case.)

Everything seems to work fine from my Windows machine.

I also tried booting from the Ubuntu live cd.. Getting packet loss even then.
I guess it could be the router, but then it shouldn't work in Windows I think.

I have checked the cable; it's not that.

**Update:**

When booting Windows on the same computer as Ubuntu I get the same problem! So I think the router is fauly. Wierd that it works from my other Windows machine though.

---

### Post by ddrichardson on 2007-08-21
Blacklist the IPV6 module. Its the only imediate difference between Windows and Ubuntu that springs to mind.

---

### Post by Jungleboss on 2007-08-22
Will try that! But please note that I get the same problem in Windows XP on the same computer. On another machine (Windows) it works though.

---

### Post by PLAY3ER on 2007-10-30
Hello, i would like to  ask for help, im having the same problem, expect, it doesn't happen on my windows partition, and my wireless is the same way, i woujld like to fix this, or Ubuntu's not going to be used, be a do alot of gamming, thanks for the replies,

PS:im aware of the post's dates and forgive for bringing it back up, but i have looked and looked,

---

