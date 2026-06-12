---
title: "Network Manager Problem"
date: 2010-11-03
forum: New to Ubuntu
---

### Post by Exotahu on 2010-11-03
I'm running 10.04 and the panel icon to control network connections disappeared, and I can't connect to networks anymore. The network settings are still there, but I cannot connect. I tried adding it pack to the panel, but it was not in the options to do so.  In attempting to fix this, I accidentally uninstalled the network manager, but I went into netroot recovery mode and reinstalled it.   Still can't get it to connect to anything and the icon is still gone. It won't even connect to a wired connection unless I use sudo dhclient3 eth0, and that'll only work for the terminal I did it in.  Is there any way to fix this aside from doing a clean install?

---

### Post by Hippytaff on 2010-11-03
Have you tried rebooting? the icon disappears on my panel sometimes and the reapears after I reboot?

---

### Post by Peter09 on 2010-11-03
The network manager icon is normally in the 'notifications' applet. (right click on the panel and select from there.

---

### Post by Exotahu on 2010-11-03
> **Peter09 said:**
> The network manager icon is normally in the 'notifications' applet. (right click on the panel and select from there.

 This fixed it!  Thank you! I had no idea it was in notifications. I thought it was gonna be something stupidly complex to do.

---

### Post by amjjawad on 2010-12-11
> **Exotahu said:**
> This fixed it!  Thank you! I had no idea it was in notifications. I thought it was gonna be something stupidly complex to do.

Dear OP,

Kindly mark this thread as SOLVED (Thread Tools).

Thank you :)

P.S.
I'm trying to help someone on this forum to get his NetworkManager back on the panel and I'm trying to find the exact solution. It would help everyone to jump on this thread as long as it's "SOLVED". That would save their time.

I appreciate your understanding :)

---

