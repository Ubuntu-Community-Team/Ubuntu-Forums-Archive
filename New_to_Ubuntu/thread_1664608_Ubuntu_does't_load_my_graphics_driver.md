---
title: "Ubuntu does't load my graphics driver"
date: 2011-01-11
forum: New to Ubuntu
---

### Post by jermza on 2011-01-11
Ubuntu sees my Nvidia driver perfectly.  I can access it easily from System > Admin.

After I've adjusted the colours and quit the application, my screen looks great.  However, Ubuntu doesn't load the setting on boot-up.  (I have to manually open and close the application.)

How do I get Ubuntu to load the settings when it starts?

**EDIT**

The application is System > Admin > NVIDIA X Server Settings

---

### Post by realzippy on 2011-01-11
You mean the settings made in "nvidia-settings"?

You have to save them...to "X Configuration file" (resolution,etc) or
to nvidia-settings-rc  (AntiAliasing,AF,Vsync..)

---

### Post by jermza on 2011-01-13
It's not working for me after the latest Ubuntu update. 

Previously, I simply saved the Nvidia file to my Documents and all was fine.  Now, I have to manually open the Nvidia app, at which point, the settings take affect.  I then save the file again and, on start up, I have to everything over again.

Any advice?

---

### Post by realzippy on 2011-01-13
Which nvidia-driver version?

When you have booted,open a terminal,run:
```
nvidia-settings -l
```
Does it set your formerly made settings?
If nothing happens,means your saved settings do not perform,it
simply means you made something wrong....
Which settings do you change exactly?

---

### Post by jermza on 2011-01-13
> **realzippy said:**
> Which nvidia-driver version?

When you have booted,open a terminal,run:
```
nvidia-settings -l
```Does it set your formerly made settings?
If nothing happens,means your saved settings do not perform,it
simply means you made something wrong....
Which settings do you change exactly?

Yes, it changes the settings to my formerly made ones.  But I have to manually activate them each time Ubuntu starts.

---

### Post by realzippy on 2011-01-13
So put this command in System/Settings/StartupPrograms...

---

