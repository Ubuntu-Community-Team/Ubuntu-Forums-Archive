---
title: "Remove Log Out, Lock Screen, Shut Down from Main Menu"
date: 2009-08-10
forum: New to Ubuntu
---

### Post by coldReactive on 2009-08-10
I was just wondering if it was possible to remove Log Out, Lock Screen and Shut Down from the Main Gnome Menu (the one that has everything in one little icon.)

If so, how do you do it?

---

### Post by synapsys on 2009-08-10
Right click the icon.
Un-check 'lock to panel'
Right click icon.
Click 'remove from panel'

To restore: Add 'user switcher' applet to panel.

---

### Post by coldReactive on 2009-08-10
> **synapsys said:**
> Right click the icon.
Un-check 'lock to panel'
Right click icon.
Click 'remove from panel'

To restore: Add 'user switcher' applet to panel.

No, I want to keep the menu there, I just want to remove the menu items I listed from the menu.

---

### Post by juancarlospaco on 2009-08-10
Reduce user privileges, so then the user cant shutdown, reboot, etc.

---

### Post by coldReactive on 2009-08-10
> **juancarlospaco said:**
> Reduce user privileges, so then the user cant shutdown, reboot, etc.

lol. Then how am I supposed to log out/etc?

---

### Post by CatKiller on 2009-08-11
If you have the User Switcher applet on your panel, the main menu items will be automatically hidden.

---

### Post by coldReactive on 2009-08-11
> **CatKiller said:**
> If you have the User Switcher applet on your panel, the main menu items will be automatically hidden.

See attachment then, they're still there.

---

### Post by CatKiller on 2009-08-11
> **coldReactive said:**
> See attachment then, they're still there.

That's what's supposed to happen, anyway, and that's what happened for me when I tried it. The only thing I can suggest is to remove the user switcher that you've got from the panel and add a new one in to see if it helps.

---

### Post by colau on 2009-08-16
> **coldReactive said:**
> See attachment then, they're still there.
How did you add shutdown/log-out option there?

---

### Post by coldReactive on 2009-08-16
> **colau said:**
> How did you add shutdown/log-out option there?

They're there by default, which I do not like.

---

### Post by Soul-Sing on 2009-08-16
Manage ```
gconf-editor
``` somehow......

---

### Post by coldReactive on 2009-08-16
> **leoquant said:**
> Manage ```
gconf-editor
``` somehow......

Searching around for menu gives the menu_bar, which is the default menu that comes with Ubuntu, not that all-in-one menu.

Searching for cust gives custom email headers.

Searching for log gives a bunch of log (various apps) and loginout (for compiz only) stuff

Searching for shut returns no results.

---

### Post by vedek on 2009-08-16
why would you want to do this. i am just curious

---

### Post by coldReactive on 2009-08-16
> **vedek said:**
> why would you want to do this. i am just curious

The all-in-one menu is too long for my tastes because of those options.

---

### Post by CatKiller on 2009-08-16
So did you remove and re-add the user switcher applet?

---

### Post by coldReactive on 2009-08-16
> **CatKiller said:**
> So did you remove and re-add the user switcher applet?

The all-in-one menu still had those options when I did that.

---

### Post by VCoolio on 2009-08-16
In gconf-editor navigate to apps > fast-user-switch-applet and uncheck "show_session_commands".

---

### Post by colau on 2009-08-16
> **coldReactive said:**
> They're there by default, which I do not like.
But this logout/shutdown menu is not in the Applications menu by default in my case.

---

### Post by coldReactive on 2009-08-16
> **VCoolio said:**
> In gconf-editor navigate to apps > fast-user-switch-applet and uncheck "show_session_commands".

Why would I want that? I want to show the session commands in the fast user switcher, but remove them from the all-in-one menu.

> **colau said:**
> But this logout/shutdown menu is not in the Applications menu by default in my case.

It shouldn't be in applications, I'm talking about the all-in-one menu... not the all-in-three menu.

---

### Post by CatKiller on 2009-08-16
Fair enough. I don't know how it achieves it, but this is what the User Switcher application is supposed to do to the main menu. I was hoping that removing the existing one would let it do so again. Finding out how it achieves it will probably be your next step to emulating that behaviour.

---

### Post by coldReactive on 2009-08-16
> **CatKiller said:**
> Fair enough. I don't know how it achieves it, but this is what the User Switcher application is supposed to do to the main menu. I was hoping that removing the existing one would let it do so again. Finding out how it achieves it will probably be your next step to emulating that behaviour.

I'll probably end up staying with the all-in-three menu from now on though.

---

