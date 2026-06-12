---
title: "How to save settings?"
date: 2009-12-28
forum: New to Ubuntu
---

### Post by PepeLapiu on 2009-12-28
Okay, I configure the Output volume in Sound Preferences at 150%.
Also, I like to add a panel at the bottom of the screen where I put my minimized windows, much like windoze users do.

But every time I shut down or restart Ubuntu, these settings are reverted back: the Output volume is back at 100% and the panel is moved to the top of the screen, stacked up together with my other panel.

How can I set these settings to be permanent so I don't have to spend time readjusting them every time I log on?

Thanx and Merry Christmas!
PepeLapiu :)

---

### Post by HarrisonNapper on 2009-12-29
Did your system come with Ubuntu pre-installed? Where are you changing the sound settings? It sounds like you might be changing it in padevchooser, but can't be sure. Are you adding a panel by right-clicking an existing panel?

---

### Post by PepeLapiu on 2009-12-29
> **HarrisonNapper said:**
> Did your system come with Ubuntu pre-installed?[/QUOTE)

Nope, I installed Ubuntu on a brand new windoze machine......dual booth in fact.

> Where are you changing the sound settings? It sounds like you might be changing it in padevchooser, but can't be sure.

In the top panel there is a volume icon, I don't remember if I put it there or if it was already there by default. When I right;click the icon, I pick "Sound Preferences" in the drop menu. That brings out a Sound Preferences window and there I change the Output volume from 100% to 150%. 

[QUOTE]Are you adding a panel by right-clicking an existing panel?

That is precisely how I do it. However the panel problem is now fixed. When I reboot the bottom panel comes back exactly where I put it before reboot. I don't know how the issue got resolved or what I did to solve it.

The only issue that remains is the Output volume which still always reverts to 100% after every reboot. I'd like to fix it and make the 150% setting permanent thought it's not a really big deal if I have to reset it every time.

---

### Post by HarrisonNapper on 2009-12-30
Hm, I use padevchooser in KDE in Ubuntu Studio (which mattered until Karmic, heh), so I'm not sure about the settings on what you're using. Mine stay when I change them in the device chooser. You can always change it by opening a terminal and running alsamixer. That should be permanent.

Cheers.

---

