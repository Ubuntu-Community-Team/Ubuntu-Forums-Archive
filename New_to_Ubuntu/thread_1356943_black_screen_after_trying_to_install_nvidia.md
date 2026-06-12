---
title: "black screen after trying to install nvidia"
date: 2009-12-16
forum: New to Ubuntu
---

### Post by heightsguy13 on 2009-12-16
i have the 9.10 on an alienware with sli compatible cards and when trying to set to normal visual effects setting in appearance preferences it had me download nvidia drivers im guessing and now when its black on the logon screen even though it will accept your password and you can hear the startup noise in the background:( have read numerous articles and none help at all

---

### Post by dearingj on 2009-12-18
Can you switch to a terminal using Ctrl+Alt+F1? If you can, try this:
1) Log into the terminal

2) Run the command ```
aptitude search nvidia | grep "i "
``` That will show you a list of installed packages with nvidia in their names. (The | is a [pipe symbol]("http://www.everyjoe.com/newlinuxuser/howto-use-the-pipe-symbol/"), not a capital I or a number 1. Also notice the space after the i)

3) Run ```
sudo aptitude remove *packagenames*
```where *packagenames* is a space-separated list of all the packages that were listed as installed, i.e. "sudo aptitude remove nvidia-settings nvidia-185 nvidia-common"

4) Reboot the computer using ```
sudo reboot
```

---

### Post by Extract_Here on 2009-12-18
did you install the proprietary drivers?

---

