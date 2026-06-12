---
title: "x11vnc and keyboard remote mapping"
date: 2014-04-01
forum: Networking &amp; Wireless
---

### Post by balubeto on 2014-04-01
Hi

I installed x11vnc server on Lubuntu 13.10 32 bit with an Italian keyboard and it is run on startup using the *display-setup-script* directive located in the */etc/lightdm/lightdm.conf* file and the **/usr/bin/x11vnc -rfbport 5900 -auth /var/run/lightdm/root/:0 -rfbauth /etc/x11vnc.pass -nomodtweak -noxrecord -shared -forever -bg** command.

The computer from which I connect has Windows 7 SP1 64-bit with the keyboard layout of the United States (EN) and I use UltraVNC viewer to connect to the Linux computer.

Now, I noticed that some symbols, typed from the Windows computer, are interpreted by the Linux machine incorrectly (ie, with other symbols).

So, considering that I can not change the keyboard layouts, how can I solve this problem?

Thanks

Bye

---

