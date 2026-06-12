---
title: "Remote Desktop Vista"
date: 2007-11-04
forum: Networking &amp; Wireless
---

### Post by RealG187 on 2007-11-04
[http://ubuntuforums.org/showthread.php?t=439733](http://ubuntuforums.org/showthread.php?t=439733)

A while back I had trouble controlling my Vista, I got ultimate (it messed up my OEM software and stuff so I have to get the OEM disks again :() but I can connect from XP, how ever there is no Aero and I cant 3D window flip, etc, but I guess RDC cant do that).

Yesterday I tried to connect from Ubuntu and it didnt work, I then used RDC5 or something like that (in terminal server I changed the setting). I did it from 7.10. The resolution on my Ubutnu machine was less than my laptop so my icons screw up, is there a way to fix that, even if I have to scroll?


however, I cannot control Ubuntu from Vista, why is this so?

---

### Post by localzuk on 2007-11-04
Ubuntu doesn't have remote desktop as a control method - as this is a proprietory system used only by Windows.

There is a program called VNC which should allow this functionality. Take a look at [https://help.ubuntu.com/community/VNC](https://help.ubuntu.com/community/VNC) for information.

Also, Aero/flip 3d rely heavily on local hardware to operate and are therefore not available via remote desktop.

---

### Post by RealG187 on 2007-11-04
I think I will go back to OEM home premium, but I have tried VNC before and it doesnt work with Vista!

Okay so to make Ubuntu a VNC server I cant goto [https://help.ubuntu.com/community/VNC](https://help.ubuntu.com/community/VNC)
To make it a cleint I can just run the same app I did before but change to protocol from RDC to VNC.

But how do I make Vista a server?

[color=red]Update[/color] 

I can control Ubuntu fine, I am surprised at the speed. I still cant control Vista though, VNC is in listening mode and the firewall has been set,


```
unable to connect to host: Connection timed out (11o)
```comes up after a while.


After I close that:
```
An error has occurred.

Reconnect in xx seconds
```
xx counts down from 30.


Details

```
VNC viewer free 4.1.1 for X - built Sep 10 2007 17:17:04
Copyright (C) 2002-2005 RealVNC Ltd.
see http://realvnc.com for information on VNC.

Sun Nov 4 13:38:41 2007
main:       unable to connect to host: Connection timed out (110)

```

[color=blue]Yet another update[/color]
After I turned on listening mode I turned it off and ran the server app again and it did the firewall thing, I finally got it to work!

how to increase the screen res on Pentium III!

---

