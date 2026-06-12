---
title: "Looking to disable pop-up messages in Ubuntu"
date: 2009-03-21
forum: New to Ubuntu
---

### Post by xg7 on 2009-03-21
When hovering over various buttons in the desktop, pop-up descriptions appear.  Is there a way to disable some/all of these?

Thanks

---

### Post by llamabr on 2009-03-21
Mine don't do that by default.  What do they say?  Can you post an pic?

---

### Post by mikewhatever on 2009-03-21
Open gconf-editor with alt+f2, gconf-editor, navigate to 
/apps/panel/global/tooltips_enabled and untick tooltips_enabled box.

---

### Post by SunnyRabbiera on 2009-03-21
These are not popups, they are tooltips.
Unless they are offering you free porn or something, you might get popups on Firefox every so often.

---

### Post by xg7 on 2009-03-21
> **llamabr said:**
> Mine don't do that by default.  What do they say?  Can you post an pic?

An example; if I hover over the panel below where my open firefox is banked, the pop-up says "Ubuntu Forums - Reply to Topic - Mozilla Firefox".

---

### Post by xg7 on 2009-03-21
> **mikewhatever said:**
> Open gconf-editor with alt+f2, gconf-editor, navigate to 
/apps/panel/global/tooltips_enabled and untick tooltips_enabled box.

Tried that already (I did a search), so I guess these aren't tooltips

---

### Post by kpatz on 2009-03-21
The tooltips appear when you mouse over something where the description (such as Firefox's title bar) is too big to fit in the space.  It can be handy if you have several instances of something and you don't know which is which.

Windows does the same thing.

---

### Post by xg7 on 2009-03-21
Ok, so they are tooltips after all.  So why didn't they turn off when I unchecked them as suggested?

Thanks

---

### Post by mcduck on 2009-03-22
> **xg7 said:**
> Ok, so they are tooltips after all.  So why didn't they turn off when I unchecked them as suggested?

Thanks

That only turns them off for the panel. There is no way to turn them off globally. (Alythough, if you use Compiz, you can make them invisible ;))

---

### Post by xg7 on 2009-03-22
> **mcduck said:**
> That only turns them off for the panel. There is no way to turn them off globally. (Alythough, if you use Compiz, you can make them invisible ;))

Strange, tooltips still appear on my panels.  Box is unchecked.
???

---

### Post by mcduck on 2009-03-23
> **xg7 said:**
> Strange, tooltips still appear on my panels.  Box is unchecked.
???

Yeah, it doesn't even affect everything in the panel, some things have tooltips any way.

It's a rather useless option, like I said the only way to get rid of those tooltips is to make them invisible. (Use the Opacity plugin to change their opacity to 0%).

---

