---
title: "network-manager bug? I can't open any application until logout"
date: 2006-11-28
forum: Networking &amp; Wireless
---

### Post by suoko on 2006-11-28
After having "claimed victory" (see [http://ubuntuforums.org/showthread.php?t=308467](http://ubuntuforums.org/showthread.php?t=308467)) for network-manager being able to connect to my fonera (which creates an encrypted wireless network), I sandly noted a BIG BUG!
When I boot the notebook which automatically logs into gnome, I can't open any application! Network manager "happily" connects to the network but the pc is useless.
I have to logout e relogin from gdm. After that, I can open any application I like.

What I thought the bug could be is that at first boot, after gnome starts, I'm asked to enter the gnome-keyring password which lets network-manager connect to the encrypted network.
That could be the cause of the problem, I guess.

Please help me!

running edgy on an asus notebook with intel pro 3945abg wireless nic

---

### Post by suoko on 2006-12-05
I dropped network-manager for "connection manager" which, although the systray applet doesn't work, is correctly connecting and working.

---

