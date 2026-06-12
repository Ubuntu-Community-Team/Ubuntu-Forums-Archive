---
title: "Gnome - Run command when there is no activity"
date: 2011-07-07
forum: New to Ubuntu
---

### Post by canam101 on 2011-07-07
I have a small script that tells the ufw firewall to lock down the computer. I can have a cron job run it at a certain time, but would prefer that it run when there has been no mouse or keyboard activity for x minutes.

Is there any way to do that?

---

### Post by frankbooth on 2011-07-07
Since it's only a small script, maybe you can check if the screensaver is active/inactive to activate/deactivate the script.

To constantly check if keyboard/mouse are doing something is probably just a PITA, dunno.

---

### Post by canam101 on 2011-07-07
> **frankbooth said:**
> Since it's only a small script, maybe you can check if the screensaver is active/inactive to activate/deactivate the script.Thanks. I can probably set it to check the screensaver every few minutes and lock down the firewall if it isn't already.

One catch: how do you check to see if the screensaver is active?

---

### Post by frankbooth on 2011-07-07
> **canam101 said:**
> Thanks. I can probably set it to check the screensaver every few minutes and lock down the firewall if it isn't already.

One catch: how do you check to see if the screensaver is active?

This should work, not using Gnome atm so can't double check :):
```

gnome-screensaver-command -q

```

---

### Post by canam101 on 2011-07-08
Thanks again, that did the trick.

---

### Post by canam101 on 2011-09-18
To follow up on this: there is a utility that locks down the computer (using the ipkungfu firewall) whenever the screensaver comes on, and unlocks it when the screensaver goes off.

It's kind of clunky but it works. It is called fwall and is at apasreader.yolasite.com.

It runs a couple of python scripts and they can probably be tweaked to work with other firewalls.

---

