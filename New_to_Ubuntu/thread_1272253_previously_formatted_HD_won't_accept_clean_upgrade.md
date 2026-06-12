---
title: "previously formatted HD won't accept clean upgrade"
date: 2009-09-21
forum: New to Ubuntu
---

### Post by Amanda HazLaPaz on 2009-09-21
This is my son's computer, a Compaq. I apologize for not knowing the details better.

The previous HD failed and a used replacement was ordered (40GB Maxtor 6E040L0). Son loaded it with first Ubuntu disc he grabbed, 7.04, not realizing it wasn't the most recent release. That install worked fine.

Soon realized he wanted 8.10 or 9.04, so he attempted to clean install an upgrade. He reported that "it didn't work". When I investigated, that meant that the install seemed to go fine (use entire disc), the login page came up fine, then the initial splash screen color of light brown showed up-- then nothing. For about one minute the light brown shows, then screen goes black and nothing changes (one hour we waited).

I checked the BIOS to make sure it was booting from the HD, and that was set correctly.

We tried the factory print of 8.10 and the home burned .iso of 9.04 with the same results-- each time install seemed to go flawlessly, reboot, remove disc, restart, login screen, colored screen, black screen.
Tried changing session with X, KDE, and Gnome. No difference.

Tried the last resort of using a disc wiper. Amazingly, that didn't work either (although he was in charge of that process and the reinstall, and he has been known to be less than careful/logical in following steps carefully and also tries to *hurry things up.*

Any diagnostics from afar? Any similar experiences?

---

### Post by QIII on 2009-09-21
Intel graphics?

---

### Post by presence1960 on 2009-09-21
sounds like a graphics problem. You want to try to install using safe graphics mode. See [here]("https://help.ubuntu.com/community/BootOptions") - scroll down to the section about F4.

If that does not work you may want to try the alternate text based installer. get it [here]("http://www.ubuntu.com/getubuntu/downloadmirrors#alternate").

---

