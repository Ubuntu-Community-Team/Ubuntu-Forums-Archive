---
title: "Dual moniters in ubuntu 10.04.1 LTS?"
date: 2010-11-01
forum: New to Ubuntu
---

### Post by Buying_Some_Time on 2010-11-01
Are there any tutorials/someone out there that can help me do this? I have tried doing it from the nivida settings thing but it won't ever show on my other monitor, it will detect it but it won't show over there any help would be great thanks.  :)

---

### Post by ubunterooster on 2010-11-01
Xinerama is often used for this: [https://help.ubuntu.com/community/XineramaHowTo](https://help.ubuntu.com/community/XineramaHowTo)

---

### Post by Buying_Some_Time on 2010-11-01
gksu nvidia-settings recognizes my monitor and my second monitor, but when I apply the new settings nothing apears on my second screen, any help? Please?

---

### Post by sandyd on 2010-11-01
> **Buying_Some_Time said:**
> gksu nvidia-settings recognizes my monitor and my second monitor, but when I apply the new settings nothing apears on my second screen, any help? Please?

post output of
```

xrandr
```

and did you restart Xorg afterwords?

---

### Post by Buying_Some_Time on 2010-11-01
> **sandyd said:**
> post output of
```

xrandr
```and did you restart Xorg afterwords?

Screen 0: minimum 320 x 240, current 1280 x 800, maximum 2516 x 945
default connected 1280x800+0+0 0mm x 0mm
   1280x800       50.0*    61.0  
   1024x768       51.0  
   800x600        52.0     53.0  
   680x384        54.0     55.0  
   640x480        56.0  
   512x384        57.0  
   400x300        58.0     59.0  
   320x240        60.0  
   2516x945       61.0  
   2451x918       51.0  



Yes, I tried restarting xorg but still nothing appeared on my other screen.

---

### Post by sandyd on 2010-11-01
> **Buying_Some_Time said:**
> Screen 0: minimum 320 x 240, current 1280 x 800, maximum 2516 x 945
default connected 1280x800+0+0 0mm x 0mm
   1280x800       50.0*    61.0  
   1024x768       51.0  
   800x600        52.0     53.0  
   680x384        54.0     55.0  
   640x480        56.0  
   512x384        57.0  
   400x300        58.0     59.0  
   320x240        60.0  
   2516x945       61.0  
   2451x918       51.0  



Yes, I tried restarting xorg but still nothing appeared on my other screen.
thats.... not good.

xorg isnt detecting your monitor.

whats the monitor connected with.

---

### Post by Buying_Some_Time on 2010-11-01
:( Oh I see, it's connected with a VGA cable.

---

### Post by sandyd on 2010-11-01
> **Buying_Some_Time said:**
> :( Oh I see, it's connected with a VGA cable.

on a seperate video card or same?
because it **should** at least show that the port in the card is unplugged (like mine)
```

Screen 0: minimum 320 x 200, current 1920 x 1080, maximum 1920 x 1920
LVDS connected (normal left inverted right x axis y axis)
   1440x900       60.8 +
   1280x800       60.8 +
   1152x864       60.8 +
   1280x768       60.8 +
   1280x720       60.8 +
   1024x768       60.8 +
   1024x600       60.8 +
   800x600        60.8 +
   800x480        60.8 +
   720x480        60.8 +
   640x480        60.8 +
DFP1 connected 1920x1080+0+0 (normal left inverted right x axis y axis) 510mm x 290mm
   1920x1080      60.0*+   50.0     30.0     25.0  
   1776x1000      60.0 +   30.0  
   1680x1050      60.0 +
   1400x1050      60.0 +
   1280x1024      60.0 +
   1440x900       60.0 +
   1280x960       60.0 +
   1280x800       60.0 +
   1152x864       60.0 +
   1280x768       60.0 +
   1280x720       60.0 +   50.0  
   1024x768       60.0 +
   1152x648       60.0 +
   1024x600       60.0 +
   800x600        60.0 +
   800x480        60.0 +
   720x480        60.0 +
   640x480        60.0 +
   720x576        50.0  
**CRT1 disconnected** (normal left inverted right x axis y axis
```

---

### Post by Buying_Some_Time on 2010-11-01
It's on the same vc, maybe it's broken?

---

### Post by corncob on 2010-11-01
> **Buying_Some_Time said:**
> It's on the same vc, maybe it's broken?

Are any pins on the cable bent over?

---

### Post by sandyd on 2010-11-01
> **Buying_Some_Time said:**
> It's on the same vc, maybe it's broken?

no, its working.

the issues could be 

a) your card doesn't have dual-head support

b) You have to use the special dual head configuration.

unfortunately, I can't help you with this because I use HDMI output only.

---

### Post by Buying_Some_Time on 2010-11-01
Ok, thank you guys for helping I'm going to buy a new VGA cable to see if that fixes it.

---

### Post by Buying_Some_Time on 2010-11-02
Lol. It was my VGA cord now I got it to work thank you guys again.

---

