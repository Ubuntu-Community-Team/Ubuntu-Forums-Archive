---
title: "How to recover top taskbar and icons in Ubuntu?"
date: 2010-05-17
forum: New to Ubuntu
---

### Post by tehowe on 2010-05-17
This might be something to consider slapping a confirmation dialogue on...

At some point, I right clicked on the top dock and my finger must have slipped, and well, the nicely setup Ubuntu bar disappeared. At the same time, a bar appeared at both the left and right of the screen!

I was able to remove those, and make a new taskbar at the top of the screen, but it starts out as a completely blank bar, and half of the bits and pieces that used to be up there aren't available from the requester where you can add new elements. EG; I can add the shut down/restart button but there's no indication of where to add the wireless indicator back in, or the Empathy/IM panel, and among a number of other things my Skype indicator is gone too, so I have no access to that program either.

Is there a guide to how to set this back to default, or do I have to reinstall the OS just to bring this back?

Thanks;
tehowe

---

### Post by tom.swartz07 on 2010-05-17
> **tehowe said:**
> This might be something to consider slapping a confirmation dialogue on...

At some point, I right clicked on the top dock and my finger must have slipped, and well, the nicely setup Ubuntu bar disappeared. At the same time, a bar appeared at both the left and right of the screen!

I was able to remove those, and make a new taskbar at the top of the screen, but it starts out as a completely blank bar, and half of the bits and pieces that used to be up there aren't available from the requester where you can add new elements. EG; I can add the shut down/restart button but there's no indication of where to add the wireless indicator back in, or the Empathy/IM panel, and among a number of other things my Skype indicator is gone too, so I have no access to that program either.

Is there a guide to how to set this back to default, or do I have to reinstall the OS just to bring this back?

Thanks;
tehowe



Heck no you dont have to reinstall for that!

Open a terminal, if you cant get the applications menu pulled up, hit ALT F2 and type
**gnome-terminal**

then enter the following line

```
rm -rf ~/.gconf/apps/panel
```

Then you should be all set after you log out and back in!

---

### Post by tehowe on 2010-05-17
> **tom.swartz07 said:**
> Heck no you dont have to reinstall for that!

Open a terminal, if you cant get the applications menu pulled up, hit ALT F2 and type
**gnome-terminal**

then enter the following line

```
rm -rf ~/.gconf/apps/panel
```Then you should be all set after you log out and back in!

Thanks - I gather .gconf is the main gnome configuration directory?

I doubt there's some single thing you can read to learn all the ins and outs of an OS that sits on top of a tool like bash - I'm glad people in this community are willing to help out as learning as you go along seems like the best (and only) way to earn your Linux wings.

---

### Post by karthick87 on 2010-05-17
Execute these commands in terminal

 	Code:
 	[COLOR=Red]gconftool-2 --shutdown
rm -rf ~/.gconf/apps/panel
pkill gnome-panel[/COLOR] 

This will restore your panels..

---

### Post by tehowe on 2010-05-17
Marking this thread as solved... either of these solutions should work for any future Ubuntunauts... thanks again.

---

