---
title: "How to remove top panel from GNOME"
date: 2010-12-17
forum: New to Ubuntu
---

### Post by racie on 2010-12-17
Hey everyone.  I'm replacing my panels with AWN so I deleted my panel, and obviously now I can't delete the top one.  I know there is a way to do this through terminal, as I found the right command before, but I can't seem to find it again.  I'm finding lots of conflicting answers on Google.  Thanks.

---

### Post by NightwishFan on 2010-12-17
This way should work, but I did not test it myself.

1. Press alt+f2
2. Type this and hit run
```
gconf-editor
```
3. Navigate to /Desktop/Gnome/Session
4. On the right it should say: "required_components_list", simply remove panel from that list, to get it back simply add it back.

---

### Post by expatCM on 2010-12-17
I use awn and decided to leave the top panel in place.  I changed the properties to Autohide instead.  The reason that I left it is that skype seems to place an icon there which is kind of challenging to reproduce in awn.

---

### Post by racie on 2010-12-17
> **NightwishFan said:**
> This way should work, but I did not test it myself.

1. Press alt+f2
2. Type this and hit run
```
gconf-editor
```
3. Navigate to /Desktop/Gnome/Session
4. On the right it should say: "required_components_list", simply remove panel from that list, to get it back simply add it back.

Thanks, it worked perfectly.  Replacing gnome-panel with avant-window-navigator seems to work also.

[quote=expatCM]I use awn and decided to leave the top panel in place. I changed the properties to Autohide instead. The reason that I left it is that skype seems to place an icon there which is kind of challenging to reproduce in awn.[/quote]
Have you tried the notification applet (systray)?

---

### Post by expatCM on 2010-12-17
> Have you tried the notification applet (systray)?

nope ....  it will not run unless you delete all other notification icons in the top panel.  For me that would be several items and if it did not work it would then be a major mess to return things to the say they are now.

---

### Post by racie on 2010-12-17
> **expatCM said:**
> nope ....  it will not run unless you delete all other notification icons in the top panel.  For me that would be several items and if it did not work it would then be a major mess to return things to the say they are now.

Well it works in the same way as the systray on the panel.  Any running applications that minimize to there will be visible along with the network manager and a battery status icon if you are running a laptop.

---

### Post by expatCM on 2010-12-18
I did not know that.  Thank you for the comment.  I will have a go :)

---

### Post by racie on 2010-12-20
Oh yeah... one more thing... the volume control applet is separate.

---

