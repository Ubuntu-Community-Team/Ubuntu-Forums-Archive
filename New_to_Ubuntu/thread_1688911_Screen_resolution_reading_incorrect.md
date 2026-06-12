---
title: "Screen resolution reading incorrect"
date: 2011-02-16
forum: New to Ubuntu
---

### Post by Oathanvil on 2011-02-16
[SIZE=3][SIZE=2]Ok not sure why its reading my LCD's so that the [/SIZE][/SIZE]XScreen 0 shows a dimension of 2960x1050 pixels (835x303 millimeters) unless its grabbing total screen area from both lcd's?

In any event the root failure is it tries to also run World Of Warcraft at 2960x1050.

Even if I go to the WTF config folder for WoW and manual change the values to 1680x1050, I can get the game to then load but the image is as tall and skinny as a Penguin....

Any help much appriciated thank you.

[ATTACH]183591[/ATTACH]

[ATTACH]183592[/ATTACH]

---

### Post by jwcalla on 2011-02-16
Apps that run fullscreen can get ugly with twinview.  I have similar problems with XBMC.

I adjusted my xorg.conf file's "Screen" section thusly:

    ```
Option         "MetaModes" "DFP: 1920x1080 +0+0, CRT: 1280x1024 +1920+0; DFP: 1920x1080 +0+0, CRT: NULL"
```So I have two screen resolutions defined there: the first is both monitors on, and the second is just one monitor on, one monitor off.  I'm then able to load XBMC and select from two available resolutions: 3200x1080 (blech) and 1920x1080.

You might want to try adding something similar to your xorg.conf and see if it works:  "DFP-2: NULL, DFP-0: 1680x1050"

Then see if WoW has an in-game option to select screen resolution.

---

