---
title: "see though terminal"
date: 2009-08-27
forum: New to Ubuntu
---

### Post by wlraider70 on 2009-08-27
sorry if this is the worng place for this question.

how do i make my terminal window see though or a picture or whatever.

---

### Post by beastrace91 on 2009-08-27
If you are using the standard gnome-terminal then goto Edit-> Preferences->Background

~Jeff

---

### Post by wojox on 2009-08-27
You have to edit compiz window transparency.

---

### Post by nothingspecial on 2009-08-27
```
Eterm --trans -x --shade=0 --scrollbar=0 --buttonbar=0 --geometry=80x52+30+30
``` 

Change the geometry to whatever you like.

---

### Post by jocko on 2009-08-27
> **wojox said:**
> You have to edit compiz window transparency.
No, gnome-terminal can be set to be transparent by it self. Just go to edit-->profile preferences-->Background and set transparency. If some compositing method is used (either compiz or metacity's compositing manager) the terminal will get true transparency, but if no compositing is used it will only get fake transparency.

---

### Post by wojox on 2009-08-27
Exactly, thats what the op asked for, see through aka true transparency.

---

### Post by jocko on 2009-08-27
> **wojox said:**
> Exactly, thats what the op asked for, see through aka true transparency.
Yes, but it can't be configured from compiz, it needs to be set up in the preferences in gnome-terminal. Compiz (or any other compositing manager) just needs to be running.

---

### Post by zerhacke on 2009-08-27
I've got transparency on the terminal and I don't have compiz.

---

### Post by Liolikas on 2009-08-27
It is pseudotransparency with double wallpaper one for terminal one for desktop.

---

### Post by transmition on 2009-08-27
If you don't want to use compiz, you can use xcompmgr instead. It is more lightweight, and to my knowledge, doesn't have the same intel issues as compiz is having right now.

```

sudo apt-get install xcompmgr

```

Then be sure to add xcompgmr to your list of startup programs.

---

### Post by wlraider70 on 2009-08-27
Thanks for all the replies.

I would like true transparency, for example so i can see this forum when entering code.

Also this lappy is pretty slow, so light weight would be good.

I'm going to try out compiz and xcompmgr


thanks

---

