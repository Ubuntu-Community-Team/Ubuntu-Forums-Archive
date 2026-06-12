---
title: "What does the &quot;Fn&quot; key do?"
date: 2010-09-02
forum: New to Ubuntu
---

### Post by zer010 on 2010-09-02
I have a keyboard for my desktop that has the "Fn" key.  I've read that it has special functions on laptops and such. I was messing with it and the arrow keys and all of a sudden my screen went to a garbled Splash then my PC shut off. 
What does the Fn key do on a desktop? I can't seem to remap it in the "Keyboard Shortcuts" menu.

---

### Post by valbaca on 2010-09-03
Try System > Keyboard > "Layouts" tab > "Options" button to adjust your keyboard settings.

To really know "what it does" try the following in a terminal
```
xev &
```

xev shows the results of user inputs. The & (ampersand) is just there to run it in the background so that it stops when you close the small window that opens with it.

---

### Post by zer010 on 2010-09-03
^ Something happened in the terminal when I pressed Fn+Down arrow.  It turned off before I could see what it was. At the top of the garbled Splash screen it was showing something about pm_op.....pci.....something....thaw : error -16
Something about a failed thaw: -16

---

