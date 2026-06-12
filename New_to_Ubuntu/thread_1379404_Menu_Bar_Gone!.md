---
title: "Menu Bar Gone!"
date: 2010-01-12
forum: New to Ubuntu
---

### Post by Javelin Dan on 2010-01-12
In my usual ham-fisted way, I apparently (accidently) hit some sort of key-stroke command that removed my menu bar from the top of my desktop. I can right-click to bring up my applications menu, but I'm still missing my drop down for my wireless connection which is my crisis of the day. Can someone please help?

---

### Post by patchwork on 2010-01-12
Alt-F2, type in xfce4-panel

---

### Post by studmf on 2010-01-12
I've done this before,
 
[LEFT][FONT=Verdana][SIZE=2]Once the Terminal window opens, enter the following command at the prompt:[/SIZE][/FONT]
**[SIZE=2][/SIZE]** 
[COLOR=#ff0000]***[SIZE=2]gconftool &#8211; -recursive-unset /apps/panel [/SIZE]***[/COLOR]
[FONT=Verdana][SIZE=2](**Remember:** T*here should be no spaces between the two dashes before shutdown.*)[/SIZE][/FONT]
[COLOR=#000000][FONT=Verdana][SIZE=2]Then enter the next command:[/SIZE][/FONT][/COLOR]
[COLOR=#ff0000]***[FONT=Verdana][SIZE=2]rm -rf ~/.gconf/apps/panel[/SIZE][/FONT]***[/COLOR]
[FONT=Verdana][SIZE=2]And enter one more command:[/SIZE][/FONT]
[COLOR=#ff0000]***[FONT=Verdana][SIZE=2]pkill gnome-panel[/SIZE][/FONT]***[/COLOR][/LEFT]
[COLOR=#ff0000][FONT=Verdana][COLOR=#000000][SIZE=2]That's it! [/SIZE][/COLOR][/FONT][/COLOR]

---

### Post by Javelin Dan on 2010-01-12
Right! - where's the xfce-4 panel?

---

### Post by Javelin Dan on 2010-01-12
I'm a virgin to all of this, and I'm not sure of the spacing. I read:   gconftool(space?)--recursiveunset(space?)/(space?)apps(space?)/(space)panel  is that correct?

---

### Post by patchwork on 2010-01-12
Alt-F2 opens the Run Program dialog box.   Type : xfc4-panel in the box and hit Run.  (Assuming you haven't re-mapped the key combination of Alt-F2 to something else.)

---

### Post by Javelin Dan on 2010-01-12
Thanks, I'll try that.

---

### Post by studmf on 2010-01-12
for the commands simply copy and paste
 
You may need to place sudo in front of the first command line

---

### Post by Javelin Dan on 2010-01-12
Thanks to all - I'll let you know how it comes out. Is there a (easy) way to lock-ot accidental key commands?

---

### Post by J V on 2010-01-12
no, no sudo... its also possible that he right click removed the panel, in which case he'll have to rebuild it (rightclick desktop add new panel...)

---

### Post by studmf on 2010-01-12
> **J V said:**
> no, no sudo... its also possible that he right click removed the panel, in which case he'll have to rebuild it (rightclick desktop add new panel...)
 
Agreed, but those commands should restore the panel even if it is removed.

---

### Post by J V on 2010-01-12
no, you're thinking if its been killed yes?

if you rightclick a panel and select remove it should wipe them all off the face of the eart... ehm... desktop...

---

