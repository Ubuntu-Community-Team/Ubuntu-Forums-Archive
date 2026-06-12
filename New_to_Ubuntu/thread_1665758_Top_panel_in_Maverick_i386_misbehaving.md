---
title: "Top panel in Maverick i386 misbehaving"
date: 2011-01-12
forum: New to Ubuntu
---

### Post by bwallum on 2011-01-12
This has been observed on 3 separate machines with latest installs of 32bit Maverick. Two from latest live cd, one from upgrade from Lucid.

Manifestation One
--------------------
The top panel is unclickable. Using Alt F2, selecting terminal then entering sudo reboot brings the system back up and running ok.

Manifestation Two
---------------------
Applications, Places and System not shown, Shut Down button (normally defaults far right) not shown and Indicator Applet Session duplicated. Using Alt F2, selecting terminal then entering sudo reboot brings the system back up and running ok.

Anybody else (a lot must be) seeing this behaviour? Anybody notice it on 64bit? (I run one 64bit Maverick and have no problems at all with it)

---

### Post by SuaSwe on 2011-01-12
Not seen any of these on mine - maybe file a bug report on Launchpad.net, if there isn't one already?

---

### Post by bwallum on 2011-01-17
Known bug, Gnome in denial, Ubuntu tearing hair out, from what I can see.

---

### Post by mastablasta on 2011-01-17
maybe a programme (not the OS) that is installed on all three (perhaps incorrectly or with a broken package) is causing this?

---

### Post by philinux on 2011-01-17
> **bwallum said:**
> This has been observed on 3 separate machines with latest installs of 32bit Maverick. Two from latest live cd, one from upgrade from Lucid.

Manifestation One
--------------------
The top panel is unclickable. Using Alt F2, selecting terminal then entering sudo reboot brings the system back up and running ok.

Manifestation Two
---------------------
Applications, Places and System not shown, Shut Down button (normally defaults far right) not shown and Indicator Applet Session duplicated. Using Alt F2, selecting terminal then entering sudo reboot brings the system back up and running ok.

Anybody else (a lot must be) seeing this behaviour? Anybody notice it on 64bit? (I run one 64bit Maverick and have no problems at all with it)

Try logging out then back in. Or in terminal ```
killall gnome-panel
```

This could be compiz related.

---

### Post by bwallum on 2011-01-17
Thanks for the shorter work around Philinux, works for me...

The bug is well documented and comes in many variants I've discovered. 

[https://bugs.launchpad.net/ubuntu/lucid/+source/gnome-panel/+bug/439448](https://bugs.launchpad.net/ubuntu/lucid/+source/gnome-panel/+bug/439448)

---

### Post by mastablasta on 2011-01-17
If it's really a Gnome bug you could try KDE or XFCE.

---

### Post by philinux on 2011-01-17
> **bwallum said:**
> Thanks for the shorter work around Philinux, works for me...

The bug is well documented and comes in many variants I've discovered. 

[https://bugs.launchpad.net/ubuntu/lucid/+source/gnome-panel/+bug/439448](https://bugs.launchpad.net/ubuntu/lucid/+source/gnome-panel/+bug/439448)

Try proving it's compiz by selecting System>prefs>Appearance>Visual Effects> NONE

---

### Post by bwallum on 2011-01-18
> **philinux said:**
> Try proving it's compiz by selecting System>prefs>Appearance>Visual Effects> NONE

I'll give it a go, one machine with NONE, the other with NORMAL. The bug is intermittent so I'll keep an eye on the machines (both in normal everyday use) for a week or so.

EDIT
Had one incident with an AMD64 Desktop - Maverick. The up and down network indicator icon was vertically split about 2/3rds from the left edge. It was blank in the last 1/3rd. Running nvidia 'current version recommended' driver, visual effects set to 'Normal'. 
Both i386 Maverick Desktop machines unchanged, one at 'Normal', one at 'None'. Both these machines using nvidia 'current version recommended' driver. Hmmm...

EDIT2
Now just over a month. With machines set with Visual Effects to None then no problem with top panel
New (to me and Ubuntu) Dell Inspiron laptop freshly installed and set to 'Normal' yielded two events of user name duplicated and no Indicator Applet Session visible to shut down the machine.
Conclusion: Visual Effects set to None yields no problem; Visual Effects set to Normal gives intermittent fault of top panel not displaying correctly.

Where to now philinux?

---

