---
title: "Wireless Suddenly Stopped Working"
date: 2008-03-30
forum: Networking &amp; Wireless
---

### Post by thetimekeeper on 2008-03-30
I'm really at a loss with this one. I use Ubuntu 7.10 and Network Manager to connect to my WPA-TKIP protected university wireless. It worked flawlessly since October of last year, and now recently it just stopped working. It would attempt to connect, the bottom light would go green, and usually the top one would go on and it would connect, but this time it never does.

I've tried removing network manager, and installing wicd, no dice. I want to reinstall network manager now using the .deb but it keeps saying it needs libc6 as a dependency. When I reboot to XP to get THAT dependency, it says a later version is already installed.

It's certainly hard when you take apt-get for granted :(. Any advice would be much appreciated.

---

### Post by prshah on 2008-03-30
> **thetimekeeper said:**
> I'm really at a loss with this one. I use Ubuntu 7.10 and Network Manager to connect to my WPA-TKIP protected university wireless. It worked flawlessly since October of last year, and now recently it just stopped working. 

It's certainly hard when you take apt-get for granted :(. Any advice would be much appreciated.

Any relevant dmesg output would be helpful; ```
dmesg | tail -20
```

bummer having to switch back and forth just to give me the output; but maybe it will help.

---

