---
title: "Root Terminal"
date: 2011-04-14
forum: New to Ubuntu
---

### Post by DGINSD on 2011-04-14
Some how I ended up with a Root Terminal entry in my applications menu, under system tools. I thought I added it through Ubuntu Tweak but now I'm realizing it may be a security concern and I want to remove it, but can't find where I added it and thus can't remove it. So my question, is this a security risk and if so how can I remove it? Also what would one use the root terminal for?

---

### Post by TeoBigusGeekus on 2011-04-14
I don't think it would work in ubuntu, would it?
Since the root account is locked, there can't be a root terminal (or not?).
Have you tried it?
Click it and tell us what it does.

---

### Post by seawolf167 on 2011-04-14
I've got one there as well, I can't remember exactly when it appeared, but I think in 10.04 (not 10.04.2) when wine (or maybe htop) created their entries in System Tools the Root Terminal also appeared.

You can remove it by right clicking the Applications menu and selecting "Edit Menus", then find the entry and remove it.

EDIT: spelling

---

### Post by ajgreeny on 2011-04-14
I don't think it is any more of a security threat than any other GUI application that needs a password.  To start it you need to enter the user password of whichever user is logged in, and that user must have membership of the admin group.  It is just like synaptic, or many other apps needing root permissions, ie, you can't use it without the password of the admin user.

Don't worry, it's not a problem!

---

### Post by Joe of loath on 2011-04-14
The root terminal button is just a shorter way to a root prompt than opening a regular terminal and typing sudo -i or sudo su. Not a security risk at all.

---

### Post by el_koraco on 2011-04-14
> **TeoBigusGeekus said:**
> I don't think it would work in ubuntu, would it?
Since the root account is locked, there can't be a root terminal (or not?).


Sure there is, it's the equivalent of typing sudo su or sudo -i in the Gnome terminal. 
Right click on the menu, edit menus, under System tools uncheck root terminal, and that's it.

---

### Post by TeoBigusGeekus on 2011-04-14
> **el_koraco said:**
> Sure there is, it's the equivalent of typing sudo su or sudo -i in the Gnome terminal. 
Right click on the menu, edit menus, under System tools uncheck root terminal, and that's it.

Ok, thanks, I didn't know that.

---

### Post by coffeecat on 2011-04-14
> **DGINSD said:**
> Some how I ended up with a Root Terminal entry in my applications menu, under system tools.

You must have accidentally activated it from the Alacarte menu editor. There's an entry for a root terminal there by default, but not activated. See my screenshot. As others have said, it's not a security risk, just a convenience if you don't want to be doing "sudo -i" every time you need to do a session of root terminal administration.

---

### Post by DGINSD on 2011-04-15
> **coffeecat said:**
> You must have accidentally activated it from the Alacarte menu editor. There's an entry for a root terminal there by default, but not activated. See my screenshot. As others have said, it's not a security risk, just a convenience if you don't want to be doing "sudo -i" every time you need to do a session of root terminal administration.

Sorry guys didn't mean to abandon my own thread. 

Your right Coffeecat that is where I activated it, thanks for reminding me.

So in order to use it I have to enter my password same as using the sudo command so theres no real security issue with having it there.

But just for clarity if I do use it, does the sudo time out still apply, or are root permissions granted for as long as I have the root terminal open?

---

### Post by Joe of loath on 2011-04-15
The sudo time out will be for 15 minutes after you type your password in, but the terminal will stay open for however long you leave it (just as a sudo -i or sudo su will do).

---

### Post by coffeecat on 2011-04-15
I *believe* the sudo timeout only applies so long as you remain in a standard terminal. Once you have a root terminal, the timeout doesn't occur.

No doubt someone will correct me if I have this wrong. :)

---

### Post by ajgreeny on 2011-04-15
> **coffeecat said:**
> I *believe* the sudo timeout only applies so long as you remain in a standard terminal. Once you have a root terminal, the timeout doesn't occur.

No doubt someone will correct me if I have this wrong. :)
No, I'm pretty sure that is correct.  It has been suggested as one way to avoid the time-out annoyance of re-entering passwords several times if doing a very long and complicated sequences of terminal actions needing root permissions.  This is specially so if you have reduced the time-out down to one or two minutes, as I have, for extra security.

---

