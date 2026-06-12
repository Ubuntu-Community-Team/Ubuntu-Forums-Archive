---
title: "Display issues"
date: 2009-08-07
forum: New to Ubuntu
---

### Post by hdrs13 on 2009-08-07
I installed 9.04 yesterday. It worked fine. I had it on my notebook and I was using an external display as well. Both displays were recognised and loaded into the correct resolutions. When I tried booting up earlier today, it gave me some display error and wouldn't show up on the external display. It took a bunch of messing around to even get to the login screen on the notebook screen. After finally logging in, it didn't recognise the laptops screen or the external. Now it only allows vga and svga resolutions on the laptop display, but I need at least 1366x768 for the laptop screen. I've tried looking at the drivers but the list shows up completely blank. What could I do to at least get the display for the laptop working at the correct resolution? I'm completely new to GNU/Linux so any help is appreciated.

---

### Post by mapes12 on 2009-08-07
It could be that your video driver has failed for some reason since the install. To check what dispaly adapter you have go Applications>Termina then type this ```
sudo lshw -C Display

``` and press enter. Post the output back here.

If you have a Nvidia adapter you may need to activate a restricted driver. To check go System>Administration>Hardware Drivers. Select the recommended one and activate it. For the canges to take effect you may have to log back into your session: Alt+Ctrl+Backspace

Any good?

---

