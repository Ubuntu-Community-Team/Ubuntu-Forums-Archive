---
title: "getting Nvidia drivers to work"
date: 2009-04-06
forum: New to Ubuntu
---

### Post by xstryker on 2009-04-06
I have Downloaded and installed the correct drivers for my video card (Geforce4 MX4000) but I am still getting the message desktop effects cannot be enabled. I have tried restarted the computer assuming a restart would enable them... but no dice, Can someone give me something else to try, I'm still a newbie to this.

---

### Post by pissedoffdude on 2009-04-06
Post the output of ```
cat /etc/X11/xorg.conf
``` and ```
glxinfo | grep rendering
```

---

### Post by spcwingo on 2009-04-06
Where did you get the driver?  Through system>admin>hardware drivers, or from the nvidia site?  If the latter, I would recommend uninstalling (instructions on how to do this through the readme included with the downloaded driver) and either using the above mentioned way or through envyng.  To install envyng (it will download the latest drivers, install them, and configure xorg for you) just type this in the terminal:

```
sudo apt-get install envyng-gtk
```

Or if you're on KDE:

```
sudo apt-get install envyng-qt
```

---

