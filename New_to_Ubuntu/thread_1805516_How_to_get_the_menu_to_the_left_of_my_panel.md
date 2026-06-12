---
title: "How to get the menu to the left of my panel?"
date: 2011-07-16
forum: New to Ubuntu
---

### Post by kramer65 on 2011-07-16
Hello,


Today I accidentally took the menu away from the top panel. With that I mean the Applications/Places/System things. I was able to add it to the panel again, but I can't get it all the way to the left, there is like 2 pixels between the menu and the left side of the screen. Now I guess you say: whatever about those two pixels, you can't even see the difference. There is however a big difference; when I now quickly go the the top left with my mouse and click, I don't get the Applications menu. I now need to go to the top left and then a tiny bit back to the right.

This is so enormously annoying when working with my system. Does anybody know how I get the menu all the way to the left side of the panel again?

Thanks!

---

### Post by josephmills on 2011-07-16
to set back to default do a ```
gconftool --recursive-unset /apps/panel && killall gnome-panel
``` in your terminal

---

### Post by amjjawad on 2011-07-16
Would you please include a screenshot?

---

### Post by kramer65 on 2011-07-16
Josephmills, thanks. That solved all, including another problem which I had for a long time but learned to deal with.. :)

---

