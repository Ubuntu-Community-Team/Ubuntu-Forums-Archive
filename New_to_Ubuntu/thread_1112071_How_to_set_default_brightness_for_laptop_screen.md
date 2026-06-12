---
title: "How to set default brightness for laptop screen?"
date: 2009-03-31
forum: New to Ubuntu
---

### Post by Paddy Landau on 2009-03-31
The default brightness for my laptop screen is set to brightest. As it's a very bright screen, I'd like the default setting to be dimmest.

Currently, I've done this by putting this line of code into my startup script:
```
xrandr --output LVDS --set BACKLIGHT 0
```That works whenever I log in first thing in the morning.

However whenever I switch user, or whenever I wake up the computer after it turns off the monitor or goes to to sleep, then it sets the brightness back to brightest.

How do I set the default brightness to dimmest? Or, how do I run that line of code whenever I switch user or wake up the computer after it's turned off the monitor?

---

### Post by Kosimo on 2009-03-31
Did you have a look into the Power Save Settings?

You can choose there the bright on power and AC

---

### Post by Paddy Landau on 2009-03-31
> **Kosimo said:**
> Did you have a look into the Power Save Settings?

You can choose there the bright on power and AC
I have Power Management (I don't see Power Save). But there's only a setting for brightness on battery, not on AC.

Perhaps it's only in Intrepid? I use Hardy.

---

### Post by Kosimo on 2009-03-31
> **Paddy Landau said:**
> I have Power Management (I don't see Power Save). But there's only a setting for brightness on battery, not on AC.

Perhaps it's only in Intrepid? I use Hardy.

Sorry, I meant power management.
So it doesn't have one while running on AC? I'm actually in my office so I can't confirm

---

### Post by Paddy Landau on 2009-04-01
> **Kosimo said:**
> Sorry, I meant power management.
So it doesn't have one while running on AC? I'm actually in my office so I can't confirm
No, there's no brightness setting on AC. There's only "Dim display when idle," but that doesn't help.

---

