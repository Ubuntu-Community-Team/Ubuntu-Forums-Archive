---
title: "Can't get native resolution"
date: 2009-06-09
forum: New to Ubuntu
---

### Post by keymoo on 2009-06-09
Hi there,

I have just installed Jaunty onto an old PC which has: Athlon XP1700+ CPU, 768MB RAM. Works fine except the video. I can't seem to change it beyond 800x600. I have tried to install the nVidia drivers by doing System->Admin->Hardware drivers and then choosing NVIDIA accelerated graphics driver (version 96) [Recommended] but when I restart, it seems to be in the native resolution but my screen is scrambled and I have to revert.

Please help! Many thanks.

---

### Post by linux4life88 on 2009-06-09
This is probably not what you want to hear but I had a similar problem and I tried everything to fix it. I had many people offer up suggestions and nothing worked. I installed driver after driver. Then when 8.10 was released I installed it and magically everything worked. Although there is a little bit of a light at the end of the tunnel, you have Nvidea graphics, I had ATI. Nvidea supports Linux better so hopefully somebody can help you get it working. But then again it might never work right until a future Ubuntu release which is what happened to me.

---

### Post by 4Orbs on 2009-06-09
Before you activate the nVidia driver, go to the display settings (not nvidia settings) and set the resolution and refresh to auto or default. Then activate the driver and reboot. If the screen is scrambled after login, but still slightly usable, go to the appearance mgr and turn off the desktop effects. If the screen is still bad but tolerable, open the nVidia settings mgr as root "gksudo nvidia-settings" and set the res and refresh to your preferred, then click the button to save your settings to the xorg.conf file. Reboot and hopefully that might have fixed something.

---

