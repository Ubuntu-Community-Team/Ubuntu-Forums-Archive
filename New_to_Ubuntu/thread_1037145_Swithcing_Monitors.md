---
title: "Swithcing Monitors"
date: 2009-01-11
forum: New to Ubuntu
---

### Post by Blueball32 on 2009-01-11
Hi

I've got a Samsung Notebook (R70) and want to plug in a Display via HDMI or VGA, but how do I switch to this device?

Thanks :)

---

### Post by utnubuuser on 2009-01-11
Hi --  Preferences>>Screen Resolution>>Detect Displays (sometimes this is enough, and the new screen is hiding behind the icon of the first srceen, - drag and drop).

You might have to add your combined resolution "width of screen A + width of screen B" to your xorg config file.

It used to be a matter of adding a line after "Display" to the effect of "virtual 2048 768".

What version of Ubuntu?

---

### Post by Blueball32 on 2009-01-11
Thanks for the answer, but the display was not activated so it didn't appear in the Screen Resolution Settings. 

I had to actvate it via the X Server Settings, now it works perfect

:)

---

