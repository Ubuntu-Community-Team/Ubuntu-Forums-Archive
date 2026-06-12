---
title: "Battery draining fast"
date: 2011-08-02
forum: New to Ubuntu
---

### Post by hsraghu on 2011-08-02
2 days back installed ubuntu also tried suse and like ubuntu . 
But it seems the battery is draining much much faster  than i was running windows vista , which I hated it.
This is on HP D6700 notebook.
Any one has experienced this kind or any tips for conserving the battery

---

### Post by skatinjj on 2011-08-02
You can search HP's website to see if their battery check program is compatible with your system.  Not sure if it will run under WINE though.

You can try calibrating the battery by letting it drain completely (let the laptiop run until the indicator says its critical) then let it charge up completely while the laptop is shutdown (not powered on).

Also, you can check power management to see what you could configure to conserve battery life.

---

### Post by Redblade20XX on 2011-08-02
Also check in the bios if WOL is active! On my dm1z, it was and drained my battery pretty quick. :)

---

### Post by skatinjj on 2011-08-02
YOu can also use the 'top' (without quotes) command in a terminal to see what percentage of the CPU and memory is being used while idle and while running applications.

---

### Post by skatinjj on 2011-08-02
> **Redblade20XX said:**
> Also check in the bios if WOL is active! On my dm1z, it was and drained my battery pretty quick. :)

+1

I would have never even thought of that seeing as I never use it and all my systems have it disabled by default.

Idea behind this is, the nic is always on and the laptop remains in a 'soft' power state so that it can receive the command to 'wake up'

---

### Post by ajgreeny on 2011-08-02
You can also install (if necessary) and then run powertop with ```
sudo powertop
``` which will tell you how much power is being used and suggest several key presses to reduce power usage, eg W, U, P.

Unfortunately, as far as I'm aware, it has to be run each session, as any changes are lost on rebooting.

---

