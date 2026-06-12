---
title: "Having problems getting wirelessly connected with Ubuntu 9.10"
date: 2010-04-23
forum: New to Ubuntu
---

### Post by Carloshz on 2010-04-23
So, let me give you some specs, here. I just installed Ubuntu 9.10. My wireless card is a Linksys WMP54G Broadcom BCM318. I uninstalled Network Manager (not sure if it was a good move) and installed wicd network manager (as I was researching online). So, I've yet to find a solution. 

When I had "Network Manager" installed, the icon in the taskbar showed that it wasn't detecting any wireless connections. The same thing is going on with wicd. 

Now, you can talk down to me, here. I'm a Windows user, primarily. So please, baby steps work, too. 

Thanks, 

Carlos.

---

### Post by undecim on 2010-04-23
If you can connect to your router with an ethernet cable, you should have wireless drivers available in System -> Administration -> Hardware Drivers.

---

### Post by anewguy on 2010-04-23
I'll bet that's really 4318?  At any rate, there are several approaches to this, as right now you don't have a working driver installed.

IF you can connect your computer to the router with hard-wire, do so, and then run the following:

-open a terminal window (Applications/Accessories/Terminal

- sudo apt-get update

- Now check under System/Administration/Hardware Drivers - it will do a search and then let you know if a driver is available.  If so, be sure it is enabled.  You will need to disconnect the hard-wire cable before you can try wireless again.

If you DON'T have the ability to hard-wire to your router, let us know.

Dave ;)

---

### Post by jaco223 on 2010-04-23
> **Carloshz said:**
> So, let me give you some specs, here. I just installed Ubuntu 9.10. My wireless card is a Linksys WMP54G Broadcom BCM318. I uninstalled Network Manager (not sure if it was a good move) and installed wicd network manager (as I was researching online). So, I've yet to find a solution. 

When I had "Network Manager" installed, the icon in the taskbar showed that it wasn't detecting any wireless connections. The same thing is going on with wicd. 

Now, you can talk down to me, here. I'm a Windows user, primarily. So please, baby steps work, too. 

Thanks, 

Carlos.

Click on System>Administration>Hardware Drivers
And see if you have the Broadcom wireless driver in there,
If you see it click on "activate"
Restart your computer and start wicd, 
wicd should see the wireless networks now.

Hope this helps.

Jaco

---

### Post by Carloshz on 2010-04-23
Ahh, it worked insanely well, guys. I was able to hard-wire it, update, and find the right driver in the hardware window. Awesome.

Thanks a bunch for the help. I will forever be indebted to you guys; or at least a beer, one day. Haha.

---

