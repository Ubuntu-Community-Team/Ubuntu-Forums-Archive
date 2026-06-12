---
title: "Manual Brightness Overwritten by Power Manager"
date: 2010-05-28
forum: New to Ubuntu
---

### Post by caecusum on 2010-05-28
Hi all,
I use my laptop in a great deal of different lighting conditions and so I frequently adjust my backlight brightness.  Is there a way to prevent the power manager from periodically resetting the brightness to it's default?  For instance, when on AC power by brightness gets reset to maximum about every couple minutes because that's what my power preferences are set to regardless of how I manually adjust using FN keys.

---

### Post by Cathhsmom on 2010-05-28
Do you know about the brightness applet that you can add to your panel?   I do not know of a way of stopping the power management from changing the brightness, but you can adjust the brightness with the brightness applet.

---

### Post by caecusum on 2010-05-29
Thanks for the idea.  Unfortunately it doesn't seem to work; if I try to adjust the slider either with the buttons or by moving the bar the widget just closes.  I'm using the binary nVidia driver and had to add some device options to xorg.conf to even get the brightness to change, which I'm sure is why it's acting strangely.

I'm open to any other ideas, though.  I'd even settle for being able to adjust the level of "dimming" that is used when the A/C adapter is unplugged.

edit: I discovered how to adjust the level of dimming in gconf-editor: apps/gnome-power-manager/backlight/

---

