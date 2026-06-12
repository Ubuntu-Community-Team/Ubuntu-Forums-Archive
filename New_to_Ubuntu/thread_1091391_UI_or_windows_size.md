---
title: "UI or windows size"
date: 2009-03-09
forum: New to Ubuntu
---

### Post by mbele3000 on 2009-03-09
My screen resolution settings are 640 x 480 and I have also set my fonts to the lowest settings. I still cant see the entire window to readjust the size (IE cant see "close" or "apply"). It sucks! how can I fix this? Help please!

---

### Post by miegiel on 2009-03-09
"System > Preferences > Screen Resolution"
On my machine anyway :)

[LIST][*]What did you try?[*]What did not work?[*]What errors did you get?[*]What hardware are you using?[*]What drivers are you using?[/LIST]

---

### Post by mbele3000 on 2009-03-12
I installed 8.04 on a comp that is using navida gforce so Im assuming after digging around that's part of the problem. I did follow a tutorial and got 800 x 600 resolution to show up in the screen resolution options. Before I was only getting 640 x 350 and 640 x 480 and that was that. So when I was opening a window it was HUGE and I could not see the whole thing to be able to hit the "OK" or "Cancel". So no errors or any thing like that just limited screen res. I am wondering if there is a way to make all your windows a specific size when they open.

---

### Post by sisco311 on 2009-03-12
Alt + Left Click and drag the window ;)

or type:
```
xrandr -s 800x600
``` in a terminal.

then install the nvidia driver([uhelp]community/BinaryDriverHowto/Nvidia[/uhelp]) and run nvidia-settings as root:
```
gksu nvidia-settings
```
set the resolution and save the changes to the X Configuration File.

---

