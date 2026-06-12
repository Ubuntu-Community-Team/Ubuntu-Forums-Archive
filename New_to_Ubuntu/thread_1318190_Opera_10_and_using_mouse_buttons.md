---
title: "Opera 10 and using mouse buttons"
date: 2009-11-07
forum: New to Ubuntu
---

### Post by mastergunner on 2009-11-07
Guys I am enjoying Opera compared to Firefox. The one thing I can't get it to do is using the mouse buttons to control the browser. Example in Firefox if I click the left button the browser goes back a page and if I click the right I go forward. How can I get Opera to do that?

---

### Post by sisco311 on 2009-11-07
Go to Tools -> Preferences -> Advanced tab -> Shortcuts -> Mouse setup -> Edit... -> Application -> New...

In the shortcut filed write: ButtonX 
in the actions  filed: Back or Forward  

In *ButtonX* X is the number of the button (left click is 1, middle click is 2 ...)

run *xev* in a terminal to get the number of the buttons.

---

### Post by mastergunner on 2009-11-07
Thanks alot Sisco. Worked like a charm.

---

