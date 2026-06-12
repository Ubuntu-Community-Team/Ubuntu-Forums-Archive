---
title: "Component out does not work, using GeForce 9400 GT"
date: 2010-04-17
forum: New to Ubuntu
---

### Post by MockY on 2010-04-17
I am trying to hook up my regular crt TV with component, but I have tried both the proprietary drivers (195.36) downloaded for nvidia.com and the drivers recommended by Ubuntu (185), and none of them detects my TV. I just removed the Windows partition where it did work, so I know the wiring is correct.

There is a button in NVIDIA X Server Settings labelled "Detect Displays), but that button does not detect my TV either. In fact, nothing happens when that button is clicked.

I had no idea it would be so problematic to send picture to a TV using component in Ubuntu, so now I need help. Does anyone know what I could do to fix this?

---

### Post by 3rdalbum on 2010-04-17
Are you booting up the computer **with** the TV turned on and on the correct AV input channel?

It shouldn't be problematic, I've done it before and it's plug 'n' play. But the TV needs to be turned on from the beginning.

---

### Post by HermanAB on 2010-04-17
Howdy,

Technically, you only need to restart X.  So log out, turn the TV on and log in again.

---

### Post by MockY on 2010-04-17
The TV has been on all along. I have tried restarts and cold boots, but nothing. On a hunch, I tested to enable the 173 drivers, and this time it detected my TV. So apparently newer drivers can't, which is very odd.

Either way, the older drivers did manage to detect the TV and I set up a twin-view. However, the colors are off. Orange becomes purple/pink, blue becomes green, and all other colors are off as well. How come this is?

EDIT: I noticed that the colors are all off even in BIOS, so this appears not to be an Ubuntu issue. However, I noticed with the older 173 driver, I had no way of increasing the resolution to 1920x1080 when I hooked it up to my HDTV. The highest resolution I could get up to with these drivers was 1024x960 making the drivers useless. I need the latest drivers, but they don't provide any TV out for component.

So what should I do now?

---

