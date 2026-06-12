---
title: "Adding extra buttons to window titlebar"
date: 2010-04-24
forum: New to Ubuntu
---

### Post by islander_810 on 2010-04-24
Installing Mac4Lin adds an additional button to the top-right corner of the titlebar which has the same functionality as right-clicking on the titlebar.
Can someone tell me how to go about adding this manually? (ie w/o having to install Mac4Lin)

Thanks

---

### Post by undecim on 2010-04-24
press alt+f2 and type "gconf-editor"

in the editor, go to Apps -> Metacity -> General. Find the "button_layout" option in the right pane and change it to include "menu"

For example, I have mine set to "menu:minimize,maximize,close", which gives me the button you described on the left corner, and the others on the right.

---

### Post by islander_810 on 2010-04-24
Thanks, I thought the "menu:" in that option was only for alignment. Are there any other things which can be added?

---

### Post by undecim on 2010-04-24
> **islander_810 said:**
> Thanks, I thought the "menu:" in that option was only for alignment. Are there any other things which can be added?

Just a spacer. I don't know of anything else, and I don't see anything else in the description from the editor.

---

