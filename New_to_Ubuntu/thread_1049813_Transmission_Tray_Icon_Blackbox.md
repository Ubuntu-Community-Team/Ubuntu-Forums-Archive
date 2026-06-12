---
title: "Transmission Tray Icon Blackbox"
date: 2009-01-24
forum: New to Ubuntu
---

### Post by lorenbr on 2009-01-24
I'm using Hardy 8.04, and I just upgraded my version of Transmission (using the deb package off their website) from 1.0something to 1.34.  The upgrade was painless, but when I reopened Transmission the icon had been lost, and it was showing instead the big blackbox that is the default icon I guess for Ubuntu.  I was able to get the right icon back in place by digging it out of the /usr/share/pixmaps/ directory, but the tray icon (enabled from the view menu) still shows up as a little blackbox, no matter what I do.  I updated the Transmission icon from the System > Preferences > Main Menu section, so I would think that I hit it at the source, but despite closing and reopening Transmission, the icon in my launcher remains correct, and the icon in my tray remains incorrect.

Anyone got a next step for me?

Thanks

---

### Post by Sam Lars on 2009-01-25
You could try the PPA version of Transmission if you want a newer version.  Add the sources line from here for Hardy:
[https://launchpad.net/~transmissionbt/+archive](https://launchpad.net/~transmissionbt/+archive)
It may play better with Ubuntu.

---

