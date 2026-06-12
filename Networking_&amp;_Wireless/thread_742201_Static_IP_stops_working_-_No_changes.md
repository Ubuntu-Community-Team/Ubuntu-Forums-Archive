---
title: "Static IP stops working - No changes"
date: 2008-04-01
forum: Networking &amp; Wireless
---

### Post by Crash90 on 2008-04-01
I have been using a static ip so that I can port forward for Bit torrent programs.

Last night, I installed a SNES emulator and upon putting it into full screen, it flaked out and I could not read or use any menu's (very blurry/stretched out).

I had to hard shutdown (as I don't know the command to minimize all applications). Upon booting back into Ubunutu, my static IP no longer works. Even to the point where it will not recgonize the router. Changing settings to DHCP works alright, but things still run slowly.

Any idea where to start? Perhaps my configuration file was changed in the hard shutdown?

---

### Post by rrwo on 2008-04-01
You can also look for changed configuration files using
```
find /etc -mtime 1
```
Check the /etc/network/interfaces file especially.

Barring that, uninstall everything that you installed: even the dependencies. (If you use Synaptic, it has a history section that helps you see the dependencies and upgrades.)

---

### Post by Crash90 on 2008-04-01
Alright - now my Static IP works. It seems my interface file was changed. However, my firefox is slow in loading pages, but a speed test shows my internet is working at the proper speed!

I also cannot access my router! The connection times out.

---

