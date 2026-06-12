---
title: "having nvidia dual screen problem"
date: 2009-09-30
forum: New to Ubuntu
---

### Post by ErikaVonMedina on 2009-09-30
I can set up dual screens but it won't stay after reboot, it goes back to default single screen.  I go to the nvidia x server settings box, select X server display configuration , configure for "TwinView"  and it does. but  I try to save it by clicking the "Save to X Configuration File"  I get "Unable to create new X config backup file '/etc/X11/xorg.conf.backup'."

I'm using an older nvidia 5200 card

---

### Post by jbrown96 on 2009-09-30
You need to have root authorization to modify /etc/X11/xorg.conf. Launch Nvidia-settings by pressing Alt+F2 in the popup box type ```
gksu nvidia-settings
``` and press enter. Now make the twinview changes and save the configuration file. You only need to launch this program as root if you want to make persistent changes.

---

### Post by steveneddy on 2009-09-30
I believe that you must open **nvidia settings** as **root** - or administrator.

In terminal, copy and paste this command:

```
gksudo nvidia-settings
```enter your password, then do your thing and then restart and see if that doesn't fix it for you.

Any questions? Please ask.

Also, check out the links in my sig. They will help you in the future.

EDIT:

Great minds think alike - and he beat me to it.

---

### Post by ErikaVonMedina on 2009-09-30
Thanks all,  worked just fine

---

### Post by steveneddy on 2009-10-01
Glad that worked.

You're welcome.

---

