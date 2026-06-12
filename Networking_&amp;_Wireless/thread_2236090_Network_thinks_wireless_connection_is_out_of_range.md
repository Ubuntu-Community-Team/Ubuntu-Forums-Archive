---
title: "Network thinks wireless connection is out of range, won't show networks"
date: 2014-07-24
forum: Networking &amp; Wireless
---

### Post by Luxx on 2014-07-24
My wireless connection IS working. I have never plugged an ethernet cord into this computer.  I am obviously online right now, but Network says my wireless connection is out of range, won't show available networks, doesn't show correct info for the wireless connection I'm using, and displays a disconnected cable icon. This has been going on for months.

I have follwed several bugs about similar issues, but those actually wouldn't connect. Mine IS connected. This is just getting really annoying, especially when the local power company has intermittent 3-25 second power outages and I can't tell if I'm connected to the internet or not after it's back on. 

Is there some way I can get Network to behave properly or is it broken? I discovered Network Manager was actually a different thing when I downloaded it and it didn't behave this way, but I couldn't get an icon for it, and can't disable or remove Network without other things breaking (Sofware Center greys out install options, etc.). Wic'd works fine and shows connections & networks properly as well, but no icon. 

If Network isn't going to behave, is there a way I can replace it, get an icon, and still have things like Software Center work?

My computer is custom built. I didn't have this issue until the last two updates of Ubuntu, and the wifi IS ON, even if it says it's out of range, so I don't think it's a hardware/driver issue. I think something in the Network GUI maybe got left out?

---

### Post by grahammechanical on 2014-07-24
> [COLOR=#000000]I discovered Network Manager was actually a different thing when I downloaded it[/COLOR]

But Network Manager is part of the default install of Ubuntu and has been for a few years. Do you know that we should only have one network manager installed at the same time? Installing Wicd will stop Network Manager from working. Run this command to see what is in the interfaces file.

```
cat /etc/network/interfaces
```

It should say this. Anything else will stop Network Manager from doing its stuff.

> # interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback


It is my understanding the Wicd makes use of the interfaces file but Network Manager does not. Wicd may not have been modified to provide an app indicator icon for Ubuntu Unity.

Regards.

---

