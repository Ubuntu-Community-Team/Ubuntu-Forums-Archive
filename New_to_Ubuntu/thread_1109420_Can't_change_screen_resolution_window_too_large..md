---
title: "Can't change screen resolution window too large."
date: 2009-03-28
forum: New to Ubuntu
---

### Post by munkedal on 2009-03-28
I am unable to get my screen resolution to a decent setting. 576 x 432 is its present setting.  I wish to change it to something higher like 1024 X 768.  The problem I have is that when I go to system >> preferences >> screen resolution I can choose "1024 X 768" in the drop down menu, but I cannot apply the changes because the button to do so is off the bottom of the screen and I just can't reach it.  Anyone have a solution?

---

### Post by mvalviar on 2009-03-28
You can  grab that window and move it so you can see the button. Use alt-leftclick and drag away.

---

### Post by LiamWilson on 2009-03-28
After selecting the resolution, press TAB 6 times, and then press enter. 

If it doesn't change, press ALT-F4 to close it, then it should do.

I opened it and counted the TAB presses just fot you! :)

---

### Post by mvalviar on 2009-03-28
If you can't move a window past the top panel, Alt-F2 and paste this ```
gconftool-2 --set /apps/compiz/plugins/move/allscreens/options/constrain_y --type bool 0
```

---

### Post by munkedal on 2009-03-28
Thank you so much for your quick replies. The first solution worked and then I tried the second and it also works. Thank you thank you.  I did not need to try the third one

---

### Post by LiamWilson on 2009-03-28
Glad to be of assistance!

---

