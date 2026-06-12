---
title: "[SOLVED] Power management: laptop LCD keeps dimming/un-dimming since update"
date: 2008-12-09
forum: New to Ubuntu
---

### Post by FountainDew on 2008-12-09
Hi, I have this minor issue that bothers me too much to keep quiet about. Here's the steps I did:

1.) Installed Ubuntu 8.10 on an ext3 formatted drive
2.) Booted Ubuntu and went into the Power management and checked the "dim LCD something or other" checkbox 
3.) downloaded some 150+ updates from the update manager, and rebooted
4.) Went back to the Power management window and the checkbox is missing

Result:
LCD monitor keeps dimming on its own and un-dimming. Any way to fix this?

---

### Post by FountainDew on 2008-12-09
Fixed: Hi, I found the solution to this problem with a little snooping around. Basically the Power Management menu was missing a few tabs and options but those options "re-appeared" when I did this:

1.) Open System > Preferences > Screensaver
2.) Click Power Management button
3.) Uncheck "Dim Display when Idle" checkbox
4.) Open System > Preferences > Power Management

Result: From then on the Power Management menu had all tabs and options available to me. It did not until I accessed it through the Screensaver menu. Odd :)

---

