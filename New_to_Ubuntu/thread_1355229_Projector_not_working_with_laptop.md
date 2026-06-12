---
title: "Projector not working with laptop"
date: 2009-12-14
forum: New to Ubuntu
---

### Post by japhyr on 2009-12-14
Hello,

I am trying to get a Toshiba Tecra M3 laptop running Ubuntu 8.04.3 to display through a projector.  System>Preferences>Screen Resolution shows a checkbox to clone the screen, but applying the settings does not send the display to the projector.  If I leave the projector set up and restart, the bar showing that ubuntu is loading shows up on the projector.  Then, just before the login screen is displayed, the projector display disappears and the login screen appears only on the laptop screen.

How do I get the computer to use the projector?

---

### Post by earthpigg on 2009-12-14
what video card is in that laptop, and what driver are you using?

---

### Post by japhyr on 2009-12-14
The video card is an "nVidia Corporation NV43 [Geforce Go 6600TE/6200TE] (rev a2)".  The driver is "Nvidia Driver Version 169.12".

I got a little further.  I installed Nvidia X Server Settings.  Using this, I can get the computer to display twin view through the laptop screen and projector.  However, the max resolution I am getting on the projector is 640x480, and I know it can go to 1024x768, which matches the laptop screen resolution.

Any suggestions how to get the full resolution out of the projector?

---

### Post by japhyr on 2009-12-15
If I turn the computer on with the projector connected, I see the ubuntu loading bar on the projector.  The loading screen uses the full resolution of the projector, but then cuts out when the login screen appears.  When I tell it to use the projector again, resolution is limited to 600x480.

Is there a way to have the computer recognize the full resolution of the projector once I have logged in?

Thanks to anyone who can offer suggestions.

---

### Post by earthpigg on 2009-12-15
hi,

give this a shot if you haven't already:

```
sudo nvidia-settings
```

click around a bit, see if that gives you better luck.


if that doesn't work... well, we learn by necessity, and that has always worked for me, so i've never been forced to manually edit xorg.conf... but that would be the next place i would look.

---

### Post by baibhav on 2012-02-28
This solved my problem, in case anybody is still looking for the solution.

[http://www.baibhav.com.np/article/6-computer-tips-a-tricks/32-projector--external-monitor-display-problem-on-ubuntu-1110-solved-.html](http://www.baibhav.com.np/article/6-computer-tips-a-tricks/32-projector--external-monitor-display-problem-on-ubuntu-1110-solved-.html)

---

