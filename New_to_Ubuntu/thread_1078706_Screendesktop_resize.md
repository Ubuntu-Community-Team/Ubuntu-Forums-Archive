---
title: "Screen/desktop resize"
date: 2009-02-23
forum: New to Ubuntu
---

### Post by Total Legend on 2009-02-23
Is there a way to resize the amount of screen space the desktop itself takes up?

I'm having an overscanning issue with Ubuntu and my HDTV. Searching for "overscan" leaves me with too many non-working solutions with my setup. So I was hoping Ubuntu simply had an option to just scale down the size of it's interface.

Any clues?

---

### Post by alexsys on 2009-05-09
HI:

I´m using a Samsung 46¨ HDTV. I found a way to solve my overscan problem. It is connected through the VGA port. The resolution on my computer is setup to 1360x768 (max supported by HDTV) and video card nvidia 8500. First I installed the restricted drivers for my card (nvidia). After installing and rebooting, load the nvidia control panel(nvidia x server settings). Use terminal: sudo nvidia-settings. Go to X server display configuration. Select the advance button. Select the desire resolution, next to the resolution is the frequency menu change from auto and select 60Hz 2. I had only two options 60Hz 1 or 2. Then press apply and see if your screen size is adjusted properly. If it is right then press Save to x configuration file and confirm. If you go black scree after applying don´t worry just wait a few seconds. Also if you don´t get proper settings try the Detect display button.

HDTVs have also some image adjustment settings for the pc port verify them too. somtimes the screen is properly resized but the image is moved from one side or the other.

---

