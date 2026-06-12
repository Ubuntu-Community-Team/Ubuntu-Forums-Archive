---
title: "Odd Compiz Setting Manager behavior"
date: 2009-01-09
forum: New to Ubuntu
---

### Post by DamonChyld on 2009-01-09
I have a eee laptop with a small screen and was trying to figure out how to move windows above the top menu bar (alt-shift-left click is not working?) and I ran across this fix on several posts:

gconftool-2 –set /apps/compiz/plugins/move/allscreens/options/constrain_y –type bool 0

It did not work for me (I ended up going into keyboard shortcuts and assigning a move window hotkey) but now I have some odd behaviour in my compizconfig settings manager window. When I switch to full screen, it will "over maximise" when clicked, and then return to normal maximisation when clicked again. Besides being annoying, this makes it so that I can not select any menus as it jumps from where I was selected. 

Hopefully this makes sense and I attached a few screenies that show the toggles. Thanks for any help!

---

### Post by marshall.robert on 2009-01-09
a temp fix would be to revert back gconftool-2 &#8211;set /apps/compiz/plugins/move/allscreens/options/constrain_y &#8211;type bool 0 but doing gconftool-2 &#8211;set /apps/compiz/plugins/move/allscreens/options/constrain_y &#8211;type bool 1

---

### Post by DamonChyld on 2009-01-12
Thanks for your response but changing the gconftool-2 to bool 1  did not correct the behaviour. Any other suggestions? It is only the compiz settings manager that has this issue and I have tried to purge/reinstall the package but to no avail.

---

