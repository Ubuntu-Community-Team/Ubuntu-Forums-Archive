---
title: "white screen after de-activating ati radeon drive"
date: 2009-07-19
forum: New to Ubuntu
---

### Post by rene8 on 2009-07-19
Hi;

I have an ATI Radeon graphics card and was running jaunty with the propietary driver available via Hardware Drivers application. It was working fine except for some freezing of the screen while playing videos fullscreen, so I tried de-activating the driver.

After re-booting, I could not login to gnome session, and insted got a white screen after the login window. The strange thing is that the session actually loads, but the screen just does not show it.

The failsafe terminal loads correctly, and even runs applications like open office or firefox browser.

So, the real question would be, how can I re-activate the driver I de-activated from the failsafe terminal?

Thanks to all that can and wish to help!

---

### Post by Sitix on 2009-07-19
If I remember correctly, you should run gdm-jockey from the Ubuntu safe mode. :) This is the program that handles the restricted drivers.

---

### Post by rene8 on 2009-07-20
Hi;

Sorry, but gdm-jockey does not seem to be anywhere! (it says 'command not found' :S) -- is there any other name for the 'hardware drivers' application to be run from the terminal?

---

### Post by rene8 on 2009-07-20
Hi;

I found that the name of the application (at least in jaunty!) is jockey-gtk. I ran it and re-activated my driver. Everything is fine again! ;)

Thank you very much, Sitix! Your post gave me the clue to find the correct name of the app.

Post if this helps someone else! ;)

Cheers.

---

