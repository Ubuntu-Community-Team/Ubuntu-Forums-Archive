---
title: "Dual Screen"
date: 2009-01-24
forum: New to Ubuntu
---

### Post by Fonrus on 2009-01-24
I am new to Ubuntu and recently installed the newest version, 8.10.  I was told that there is now no "/etc/X11/xorg.conf" in the newest version of ubuntu. If I were to want a dual screen setup, how would I go about this, I  have the newest proprietary nvidia drivers, and its designed to edit the xorg.conf file,  which there is none of now.

---

### Post by emarkd on 2009-01-24
The widget at System > Preferences > Screen Resolution will attempt to enable dual screen output for you.

---

### Post by Fonrus on 2009-01-24
Yes, but since i installed the Nvidia drivers it just makes that app useless, and it wont even recognise monitors, whereas before I installed the drivers it did

---

### Post by emarkd on 2009-01-24
I didn't know.  I don't have nvidia hardware.  Maybe someone with more knowledge of the situation will come along soon.

---

### Post by overdrank on 2009-01-24
> **Fonrus said:**
> I am new to Ubuntu and recently installed the newest version, 8.10.  I was told that there is now no "/etc/X11/xorg.conf" in the newest version of ubuntu. If I were to want a dual screen setup, how would I go about this, I  have the newest proprietary nvidia drivers, and its designed to edit the xorg.conf file,  which there is none of now.

You can use nvidia-settings ```
gksu nvidia-settings
``` then setup your dual screens.

---

### Post by Fonrus on 2009-01-25
When I do that it tries to write to the xorg.conf file, of which it says it cannot find.

---

### Post by wylfing on 2009-01-25
Using nvidia-settings is definitely the way to set up dual screens with the nvidia driver.

I find it curious that you have no /etc/X11/xorg.conf at all. I am writing this post on an nearly pristine 8.10 installation and xorg.conf is present. It doesn't have much in it anymore, but it's still there. Unfortunately, my dual-screen kit is still running 8.04 so I can't confirm first-hand that all's the same in 8.10.

However, some uestions:
[LIST]
[*]Did you upgrade from a previous installation, or install fresh from CD?
[*]Are you sure you are using the nvidia driver?
[*]How did you install that driver?
[/LIST]

---

### Post by overdrank on 2009-01-25
> **Fonrus said:**
> When I do that it tries to write to the xorg.conf file, of which it says it cannot find.

Ok are you trying separate x or twin view?

---

### Post by Fonrus on 2009-01-25
It was a fresh install from an ubuntu 8.10 live cd, I am sure that I am using the nvidia driver because I used the hardware manager to download the nvidia drivers (proprietary). I would like to have seperate x, or the one that each screen is a separate desktop.

---

### Post by wylfing on 2009-01-27
How about reconfiguring the xorg server. That should generate an xorg.conf file.
```
sudo dpkg-reconfigure xserver-xorg
```

---

