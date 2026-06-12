---
title: "screen dimming"
date: 2009-11-23
forum: New to Ubuntu
---

### Post by pendulum101 on 2009-11-23
is anyone having a problem with the screen dimming in 9.10 for some reason even when i set it so that it never dimms or fades to black, so does anyone know how to fix this problem?

---

### Post by ukripper on 2009-11-23
Is it on Desktop/laptop?

If laptop, what make is it? Are your function keys working?

---

### Post by pendulum101 on 2009-11-23
> **ukripper said:**
> Is it on Desktop/laptop?

If laptop, what make is it? Are your function keys working?

its a laptop DELL INSPIRON 6400 yes it is but i cant understand what the difference is i have only just upgraded to 9.10 from 9.04

---

### Post by ukripper on 2009-11-23
Put System-->Preferences-->Power Management to 2 hours instead of Never. 

See if it still dims now?

---

### Post by pendulum101 on 2009-11-23
> **ukripper said:**
> Put System-->Preferences-->Power Management to 2 hours instead of Never. 

See if it still dims now?

yes it does whether or not it is plugged in or not its annoying when watching a movie in particular thanks for your help

---

### Post by hilljb on 2009-11-23
I can confirm this behavior on a Lenovo U450p with Xubuntu 9.10 and compiz.

Regardless of my power management settings, the screen will dim. On battery power, the screen will dim after x minutes. On AC power, the screen remains lit fully after x minutes, but then dims once I touch the touchpad or keyboard. My keyboard function buttons fail to bring the screen back to original brightness. (In fact they seem entirely out of order, while my volume function buttons are operable.)

Upon opening power management options, the screen comes back to original brightness.

---

### Post by Don1500 on 2009-11-23
apt-get install caffeine

---

### Post by Madel on 2009-11-23
i have experience that while watching movies.

fixed it by disabling the screen saver. 
there's this option in screen saver settings that activates the screen saver when computer is idle. just uncheck that settings.

---

