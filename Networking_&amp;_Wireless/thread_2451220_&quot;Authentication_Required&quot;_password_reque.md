---
title: "&quot;Authentication Required&quot; password request loop on Ubuntu 20.04"
date: 2020-09-29
forum: Networking &amp; Wireless
---

### Post by catalysten on 2020-09-29
[COLOR=#242729][FONT=Arial]I have a dual-boot laptop (Surface Book 1) that can run both Windows and Ubuntu. Two days ago, on Saturday, everything was working fine. Now, only Windows can connect. On Ubuntu, I can see the wifi network, and I can attempt to connect, but each time it bounces me back to the "Authentication Required" page where I reenter the password.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]
I've tried restarting the router, turning my computer completely off and on, and verifying (many times) that I'm using the correct password. Elsewhere on this forum, I found a script for posting internet data ([/FONT][/COLOR]https://github.com/UbuntuForums/wireless-info)[COLOR=#242729][FONT=Arial]. Perhaps it's still useful! I've attached its output here.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]
This appears to be a problem specifically between Ubuntu and my Xfinity wifi. When I turn my phone into a hot-spot, it connects just fine.[COLOR=#222222][FONT=Verdana] 
[/FONT][/COLOR][/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]What can I do to resolve this? (And thanks for taking a look!)[/FONT][/COLOR]

---

### Post by catalysten on 2020-09-30
I figured out what the problem was!


I had updated my linux kernel on Saturday, and that had overwritten my (fairly ancient) special surface-book linux kernel that I got from Jakeday's git repository. To fix the problem, I got the newest, top-of-the-line kernel from here:
[https://github.com/linux-surface/linux-surface](https://github.com/linux-surface/linux-surface)


I had to make sure to follow both its installation instructions ([https://github.com/linux-surface/linux-surface/wiki/Installation-and-Setup](https://github.com/linux-surface/linux-surface/wiki/Installation-and-Setup)) and sign the kernel using their premade public key & associated instructions ([https://github.com/linux-surface/linux-surface/wiki/Secure-Boot](https://github.com/linux-surface/linux-surface/wiki/Secure-Boot)).


It's so nice to be done with this!

---

