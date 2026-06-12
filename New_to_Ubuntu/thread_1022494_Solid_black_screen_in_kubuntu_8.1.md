---
title: "Solid black screen in kubuntu 8.1"
date: 2008-12-26
forum: New to Ubuntu
---

### Post by gatekeeper53 on 2008-12-26
I was looking around KDE4 on my Inspiron 6000 laptop and saw where to click for desktop enhancements. I stayed with the default choices and clicked OK. I saw a brief flash of the screen talking about if you like your new desk top then the screen went black and stayed that way. When I try to boot I get to the login screen. Past that the screen goes white the black and stays that way. I can do a console login but where do I need to go and what do I need to edit to undo this setting?

---

### Post by abn91c on 2008-12-26
> **gatekeeper53 said:**
> I was looking around KDE4 on my Inspiron 6000 laptop and saw where to click for desktop enhancements. I stayed with the default choices and clicked OK. I saw a brief flash of the screen talking about if you like your new desk top then the screen went black and stayed that way. When I try to boot I get to the login screen. Past that the screen goes white the black and stays that way. I can do a console login but where do I need to go and what do I need to edit to undo this setting?
sudo apt-get remove compiz
sudo apt-get remove compiz-core

---

### Post by oilchangeguy on 2008-12-26
> **gatekeeper53 said:**
> I was looking around KDE4 on my Inspiron 6000 laptop and saw where to click for desktop enhancements. I stayed with the default choices and clicked OK. I saw a brief flash of the screen talking about if you like your new desk top then the screen went black and stayed that way. When I try to boot I get to the login screen. Past that the screen goes white the black and stays that way. I can do a console login but where do I need to go and what do I need to edit to undo this setting?

try ctrl alt F12 or ctrl alt F7. this should turn off desktop effects. then go in and uncheck desktop effects.

---

### Post by gatekeeper53 on 2008-12-26
tryed ctrl alt F12 at various points during the boot with out any luck. The best it got was a black screen with a flashing underscore at the top left.

Neither compiz or compiz-core were found to be installed.

What's next? This is killing me to have to use my wife's widoze machine for help!!

---

### Post by oilchangeguy on 2008-12-26
> **gatekeeper53 said:**
> tryed ctrl alt F12 at various points during the boot with out any luck. The best it got was a black screen with a flashing underscore at the top left.

Neither compiz or compiz-core were found to be installed.

What's next? This is killing me to have to use my wife's widoze machine for help!!

i edited my post. once it running, not at boot, if ctrl alt f12 does not work. try crtl alt f7.

---

### Post by gatekeeper53 on 2008-12-26
> **oilchangeguy said:**
> i edited my post. once it running, not at boot, if ctrl alt f12 does not work. try crtl alt f7.

Neither ctrl alt f12 or crtl alt f7 get the screen back. I waited until I heard the tones at the end of the desktop loading to try them.

---

