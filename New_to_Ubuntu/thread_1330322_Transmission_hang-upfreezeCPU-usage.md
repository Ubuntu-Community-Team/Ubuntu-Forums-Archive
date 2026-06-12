---
title: "Transmission hang-up/freeze/CPU-usage"
date: 2009-11-18
forum: New to Ubuntu
---

### Post by Sceiron on 2009-11-18
Hello,
when using transmission the programs tends to get hang ups, and i have to restart i to get it to work properly.

Looking at CPU usage when only transmission is running,CPU1 is running at 100%. And the 100% switching back and forth between my to CPU's. When i shut down transmission, all CPU usage drop to 1-5%.

When i look at processes (system monitor) i see transmission only using 2% CPU, but sometimes gets the waiting channel message:
Futex_wait__queue_me or something. 

I know I just can install i.e. Deluge, but i wanna know why this happens, or at least try to.

---

### Post by ukripper on 2009-11-18
That is strange. Transmission works perfectly on 3 testing desktops running 9.10 for me.

Can you report this as a bug on launchpad - [https://launchpad.net/](https://launchpad.net/)

---

### Post by Sceiron on 2009-11-18
Not sure if its Transmission or some cofiguration that makes the problem.
Attached is the output from the Message Log.

Seems to be a problem with transmission calculating the check sum of the downloaded piceces.

Or could it be the torrent?
Dont think so because it happened with other torrents as well.

---

