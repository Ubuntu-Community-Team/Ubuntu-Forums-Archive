---
title: "Unacceptable monitor resolution"
date: 2009-03-18
forum: New to Ubuntu
---

### Post by JerryI on 2009-03-18
My Nvidia settings for my monitor have been clobbered and the resolution is so low that when I issue sudo nvidia-settings, all the control buttons are off screen and I cannot set a suitable resolution.  What can I do to remedy the problem?

---

### Post by finer recliner on 2009-03-18
two things to try:

1) rename your ~/.nvidia-settings-rc file to something else. when you reboot, run nvidia-settings again. nvidia-settings will see that your saved config file is missing and it will create a brand new one for you (hopefully what ever problem you were having was caused by something in that config file). If you want to restore the original config file, just change its name back to .nvidia-settings-rc (overwritting the new one that was created and reboot)

2) reconfigure your xserver. there is a command to automatically set it up in the comment section of your /etc/X11/xorg.conf file.

---

### Post by mcduck on 2009-03-18
> **JerryI said:**
> My Nvidia settings for my monitor have been clobbered and the resolution is so low that when I issue sudo nvidia-settings, all the control buttons are off screen and I cannot set a suitable resolution.  What can I do to remedy the problem?

Use Alt+left mouse button to move the dialog so that you can set the resolution.

Alt+left button allows you to move a window from any point in the window (instead of just the titlebar). Alt+middle button resizes the window.

---

