---
title: "Window border and compiz lag problem"
date: 2009-01-15
forum: New to Ubuntu
---

### Post by Bigbob22 on 2009-01-15
I was trying to record a video of my desktop using a desktop recorder and when i try to view the folder the video was in my computer started lagging big time. So i restarted and pressed alt + F2 and typed ```
metacity --replace
``` and windows with no borders (which usually never happens). I then typed the same code in the terminal and got my windows back. whats going on??

---

### Post by abn91c on 2009-01-15
compiz is not happy in 8.10, many posts in the forums about that. It may be time to "divorce" compiz and desktop effects.

---

### Post by Bigbob22 on 2009-01-15
I have 8.04 and I have had compiz for a few months.

---

### Post by Bigbob22 on 2009-01-16
When run ```
metacity --replace
``` in the terminal it works,but i get this message:
```
Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x3000021 
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.
```

Please help

---

### Post by Bigbob22 on 2009-01-16
Please help

---

### Post by awthomp on 2009-01-16
Try installing the compiz-fusion icon:

```
sudo apt-get install fusion-icon
```

This will allow you to easily switch between Metacity and Compiz.

Also, for lag issues, the easiest way to solve these are to:

1.  Open the Compiz configuration manager
2.  Click "General Options"
3.  Navigate to the "Display Settings" tab
4.  Uncheck "Detect Refresh Rate"
5.  Manually adjust the refresh rate to that of your monitor
6.  Check "Sync to VBlack"
7.  Change the resolution on the "Outputs" to that of your monitor

Compiz should now be smooth.  Hope this helps!

---

