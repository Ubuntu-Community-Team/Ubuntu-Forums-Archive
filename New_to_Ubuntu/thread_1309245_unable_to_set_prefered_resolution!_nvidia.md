---
title: "unable to set prefered resolution! nvidia"
date: 2009-11-01
forum: New to Ubuntu
---

### Post by xcitergr on 2009-11-01
Hello I have downloaded and using ubuntu [COLOR=Blue][B]9.10 karmic koala 64-bit,
my graphics card is the geforce 9400, nvidia.[/B] [/COLOR]I have this problem, I wanna set my pc's resolution to 1280*1024 and [COLOR=Red]**I can not find that option on the list** [/COLOR]of available resolutions!!!!!! I have checked the drivers and there is no problem with them, I have the latest version. There is actually a resolution higher than the one I want but it is 4:3 which is not the proper for my display.

**[FONT=Arial][SIZE=2]*[COLOR=Purple]So is there a way to add the prefered resolution to the table of available resolutions???[/COLOR]*[/SIZE][/FONT]**

please keep it simple and detailed because i am not THAT experienced user yet. ;)

a big thank you in advance and whoever helps me resolve this problem gets a :popcorn:

---

### Post by mhh91 on 2009-11-01
the resolution can be set from Nvidia's control panel


press Alt+F2 and type nvidia-settings

---

### Post by xcitergr on 2009-11-01
when i press alt+ F2 it says that there is no such thing as nvidia-settings! so propably this is my problem...what do you propose?

---

### Post by JBAlaska on 2009-11-01
Do You have the restricted drivers installed? check, System, Administration, NVIDIA X Server Settings

Then you should see this [[IMG]http://img301.imageshack.us/img301/3598/xsettings2.th.png[/IMG]](http://img301.imageshack.us/i/xsettings2.png/)

If you don't have that menu entry you should install the (Recommended)restricted drivers at System, Administration, Hardware Drivers

---

### Post by lokutus25 on 2009-11-03
Well...I had a nvidia 8400 and worked fine in Ubuntu 9.04 and Ubuntu 9.10. Even in xinerama with two monitor.
Now I changed with a nvidia 9400 GT and I can't no more find a nvidia.ko suitable for my video card. Does someone knows which package have I to install?!

---

