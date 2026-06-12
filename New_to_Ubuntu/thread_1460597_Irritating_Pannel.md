---
title: "Irritating Pannel"
date: 2010-04-23
forum: New to Ubuntu
---

### Post by orphanlast on 2010-04-23
Okay. I made a panel that's set to auto-hide and I also made it a short panel to the left of my screen. Well, it did the auto hide but now it won't auto-come-back. I've restarted my computer to see if that would help. Is there something in the terminal that I can type in to get this sucker to just permanently die?

I don't think I want that Panel any more in the first place.

---

### Post by pj_kare on 2010-04-23
Press Alt+F2.

Type [COLOR=Blue]gconf-editor[/COLOR] in the window and click run.
Then navigate to /apps/panel/toplevels/

Your panel should be one of the numbered panels listed panel_0, panel_1 etc.
(The ones labelled bottom and top are obviously the bottom and top panels ;))

Uncheck auto_hide in the right window.

Right click on panel (if it apppears) and select delete :P

---

### Post by orphanlast on 2010-04-23
Sweet. Problem solved.

---

### Post by orphanlast on 2010-04-23
What is it that ALT+F2 did? Because it just isn't the same thing when I typed it into the terminal. There were only slight differences between the two.

---

### Post by demuxer on 2010-04-27
hey guys, I dont know how to ask this question, but i like to have this panel in the center, but here the AUTOHIDE option never works, so I click the arrow (up/down) to hide/show it

but I want to know how to config a shortkey to make this, I can use alt+f1  to make it appear(loading Applications Menu), but I need to close it and i dont want to use the mouse to click the arrows, any help?
[[IMG]http://imgur.com/LnoRh.png[/IMG]](http://imgur.com/LnoRh.png)

---

### Post by paultag on 2010-04-27
> **demuxer said:**
> hey guys, I dont know how to ask this question, but i like to have this panel in the center, but here the AUTOHIDE option never works, so I click the arrow (up/down) to hide/show it

but I want to know how to config a shortkey to make this, I can use alt+f1  to make it appear(loading Applications Menu), but I need to close it and i dont want to use the mouse to click the arrows, any help?
[[IMG]http://imgur.com/LnoRh.png[/IMG]](http://imgur.com/LnoRh.png)

You, sir, win the internets.

As for that issue? Damn. I don't think I have ever seen that before. Give the gnome-panel guys a bug report upstream. 5 bucks say that this was a special case they never even considered.

---

