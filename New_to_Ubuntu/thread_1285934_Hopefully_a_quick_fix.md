---
title: "Hopefully a quick fix"
date: 2009-10-08
forum: New to Ubuntu
---

### Post by lilredcougar07 on 2009-10-08
So, I was going to use the Mac4Linux theme or whatever it is, but I didn't really know how to do it, so after downloading and extracting, I double clicked on one of the shell documents. The appearance of my browser and stuff changed, but I wanted to change it back to my original theme until I read how to use it correctly. So I went back in to my appearance settings and changed it back to a default theme that ubuntu comes with. The only problem is, is that my close, minimize and maximize buttons are still on the left side of all my programs, like they would be if I had continued to use the Mac4Linux theme. Can anyone help me out with this to get it back to normal? It would be greatly appreciated.

---

### Post by howefield on 2009-10-08
Press Alt + F2, type gconf-editor and hit Enter.

Navigate to apps > metacity > general option in the left window and then find the button_layout option in the right window.

Double click this option and set its value to menu:minimize,maximize,close

---

### Post by lilredcougar07 on 2009-10-08
Thanks so much! I knew this would be a quick fix. :) 

How do I change this to solved?

---

### Post by howefield on 2009-10-08
> **lilredcougar07 said:**
> How do I change this to solved?

You're welcome, I think the solved feature is back, in thread tools ?

---

