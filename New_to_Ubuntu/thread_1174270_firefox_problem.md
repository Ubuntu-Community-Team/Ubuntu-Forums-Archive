---
title: "firefox problem"
date: 2009-05-30
forum: New to Ubuntu
---

### Post by Zom-b on 2009-05-30
I did a fresh install of Xubuntu on my fiance's computer and everything is working fine, except that every so often firefox opens like a thousand pop ups that all say
```

Pressing F7 turns Caret Browsing on or off. This feature places a moveable cursor in web pages, allowing you to select text with the keyboard. Do you want to turn Caret Browsing on?

```

and it has yes and no, and a check box to never show it again, but it keeps doing it regardless of what I have tried, any ideas?

---

### Post by Didius Falco on 2009-05-30
Hi,

You can try typing ```
about:config
``` in a Firefox tab and then search for "caret".

I don't have that problem, and my settings are:

```
accessibility.browsewithcaret;false
accessibility.warn_on_browsewithcaret;true
bidi.edit.caret_movement_style;2
layout.selection.caret_style;0
```If that doesn't do the trick for you, you could try the **keyconfig** extension and set it to some key that you never get near. I've never used it, but it might be worth a look:

[http://www.pcauthority.com.au/Download/113084,keyconfig-firefox-addon.aspx](http://www.pcauthority.com.au/Download/113084,keyconfig-firefox-addon.aspx)

I hope this helps...

Regards,

Didius

---

### Post by Zom-b on 2009-05-30
no, that didn't help, the craziest thing is it's not even when I am near the f7 key, it just pops up out of nowhere, I hope I get it fixed, I'd rather not turn her off to linux right away because of something like this lol

---

### Post by freeman2000 on 2009-05-31
Try this.... in Firefox go to the Menu Bar and click on "Edit" and then click on "Preferences".   In the window that opens, click on the "Advanced" tab, then click on the "General" tab, and in the "Accessibility" section, make sure that the item titled "Always use the cursor keys to navigate within pages" is unchecked.  This works the same as F7.  Good luck.

---

