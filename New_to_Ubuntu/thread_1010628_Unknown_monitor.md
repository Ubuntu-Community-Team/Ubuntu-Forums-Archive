---
title: "Unknown monitor"
date: 2008-12-14
forum: New to Ubuntu
---

### Post by alon_lhv on 2008-12-14
I've just upgraded from Ubuntu 8.04 to 8.10, and it fixed my wireless problem, but two new problems had arrived. I want to focus one: my monitor is not recognized, although it was well recognized in the 8.04.

The screen resolution is 1024x768 but because the monitor is not recognized, it is set to be 800x600. 
I have an old IBM ThinkPad T20. 

I checked the forum and tried 2 suggestions with no good results:

1. Added to /etc/X11/xorg.conf :
```
 SubSection "Display"
        Depth        16
        Modes      "1024x768" "800x600" "1280x1024"
 EndSubSection

```
In this case, after restart Ubuntu refused to start itself, and reported a monitor problem. I had to restore the file in order to fix it and go back to my ugly 800x600 resolution.

2. Tried : sudo dpkg-reconfigure -phigh xserver-xorg
Nothing really changed.

So, what can I check next? How can I know which monitor driver should I install, and how can I install it?

Thanks.

---

### Post by alon_lhv on 2008-12-14
The problem was solved. I added this to "Monitor" section:

HorizSync       31.5 - 48.5
VertRefresh     50-70

:)

---

