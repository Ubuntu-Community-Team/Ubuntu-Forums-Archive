---
title: "how to add a custom resolution to the display panel?"
date: 2009-12-09
forum: New to Ubuntu
---

### Post by JamesParnell on 2009-12-09
is it possible to add resolutions to the drop down list in the "display" window?

if not can one be added using Xrandr?

i ask because 1024x600 is not big enough and some windows overhang the screen (and alt+drag is annoying)

at the minute im using 
```
xrandr --output LVDS1 --mode 1024x600 --scale 1.10x1.10
```
to shrink everything to fit, but it would be much better to have a fitting resolution..

---

### Post by JamesParnell on 2009-12-09
quick other question, where is xorg.conf in karmic...ive ran

```
gedit /etc/X11/xorg.conf
``` 
and didnt get the file

---

### Post by Sir Jasper on 2009-12-09
Google my posts in the last 14 days and when you find a thread with a resolution query about 1024 x 768 look at post # 16 on page two and you should find a method to set up a single or multi resolution launcher which may well work.

I am not available to answer any supplementary question(s).

---

### Post by hobo14 on 2009-12-10
Here is a step by step howto, start to finish: [http://ubuntuforums.org/showthread.php?t=1346125]("http://ubuntuforums.org/showthread.php?t=1346125")

---

### Post by mikewhatever on 2009-12-10
1024x600 is a resolution used in most of the 9-10 inch netbooks currently on the market. Usually, that is also their default and maximum resolution because their screens can't go any higher. You haven't revealed much info, but if that's your case, I think you are out of luck. On the other hand, if you are using a 24 inch display with that resolution, one of the howtos above should help.

---

### Post by JamesParnell on 2009-12-10
nope, Nc10 netbook.

ok then thanks, i guess i will live with rescaling the size for now :P

thanks much for your help

---

