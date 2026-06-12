---
title: "Shut Down"
date: 2011-06-29
forum: New to Ubuntu
---

### Post by createdcreature on 2011-06-29
Sometimes, when I try to shut down my machine, it does not shut down, so I have to unplug it from the socket. Do you have any idea why this is? I use Ubuntu 10.04, not 11.04, and dual boot with XP.

---

### Post by donny.davis on 2011-06-29
try this one```
sudo shutdown now
sudo poweroff now
sudo shutdown -P
```

---

### Post by amjjawad on 2011-06-29
> **Robert Moyse said:**
> Sometimes, when I try to shut down my machine, it does not shut down, so I have to unplug it from the socket. Do you have any idea why this is? I use Ubuntu 10.04, not 11.04, and dual boot with XP.

Have the same issue with my PC.

I log out first then shutdown and it works most of the time.
Don't use that PC now so I don't care much to fix this issue. It comes and goes for some weird reason and yes, Ubuntu 10.04 is installed.

---

### Post by laidback on 2011-06-29
I've had a problem that would appear to relate to this, I found that if I had Open Office Quickstarter running I couldn't shutdown (it's the same for the replacement to OOo), I had to logout and shutdown from there. The solution was to turn off Quickstarter:-

Run OOo Word (or any other OOo app)
Choose Tools>Options>Memory
Uncheck "Enable systray Quickstarter"

In versions 11.x I believe that Quickstarter is enabled by default.

---

### Post by createdcreature on 2011-07-03
Still not working....................

---

### Post by laidback on 2011-07-03
Sorry but I don't have any other ideas right now.

---

### Post by CatKiller on 2011-07-03
FWIW, you don't need to unplug it. Holding the power button for 5 seconds will turn it off.

The problem is that your motherboard isn't responding to the signal to power down, probably because of a buggy BIOS. Firmware updates and/or BIOS settings may help, but it's not too big a deal to just hold the button for a bit.

---

### Post by createdcreature on 2011-07-04
It works now that I have changed the ACPI settings in the BIOS!

---

### Post by laidback on 2011-07-04
That's good to hear.

---

### Post by amjjawad on 2011-07-04
> **Robert Moyse said:**
> It works now that I have changed the ACPI settings in the BIOS!

Great :)

Could you please explain how exactly did you fix it so everyone else will read your thread, will understand how did you manage to fix it :)

Thanks!

---

### Post by createdcreature on 2011-07-04
Turned on the 'Force ACPI Shutdown' in the BIOS.

---

