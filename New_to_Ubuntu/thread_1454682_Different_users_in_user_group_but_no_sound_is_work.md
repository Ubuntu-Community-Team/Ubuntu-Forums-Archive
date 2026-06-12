---
title: "Different users in user group but no sound is working and no nvidia settings"
date: 2010-04-15
forum: New to Ubuntu
---

### Post by Alt-A on 2010-04-15
I am a newb I can't get ubuntu to work correctly I am having trouble with sound, and I can not get nvidia x server setting to work in one my other user accounts... please help.

---

### Post by lidex on 2010-04-15
Try running
```
nvidia-xconfig
``` in a terminal and reboot.
For sound will need some info. Right-click the alsa-info script link in my sig and "save as" to your user folder. Then run this command in a terminal:
```
sudo bash utils_alsa-info.sh
```
Enter your user password when prompted. Provide a link for the output or post it here using code tags.

---

### Post by Gone fishing on 2010-04-15
It would seem that you haven't activated the nvidia driver.

System >  Administration > Hardware drivers then select the driver and activate.

---

