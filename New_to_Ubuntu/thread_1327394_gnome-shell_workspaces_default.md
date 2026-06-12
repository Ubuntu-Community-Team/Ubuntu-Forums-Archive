---
title: "gnome-shell workspaces default"
date: 2009-11-15
forum: New to Ubuntu
---

### Post by coldReactive on 2009-11-15
Is there any way to add a default number of workspaces to gnome shell? Or do I have to keep adding them manually when I want more?

---

### Post by Jon Monreal on 2009-11-15
I'm not exactly sure what you're asking for; could you help clarify?

What do you mean add a default number of workspaces? Wouldn't you have to change the amount as your needs change anyways?

Thanks.

---

### Post by coldReactive on 2009-11-15
> **Jon Monreal said:**
> I'm not exactly sure what you're asking for; could you help clarify?

What do you mean add a default number of workspaces? Wouldn't you have to change the amount as your needs change anyways?

Thanks.

Nope, I always want four.

---

### Post by Jon Monreal on 2009-11-15
I'm not certain that this is what you want, but you could right-click on the workspace switcher and select "Preferences". One there, change "Number of workspaces" to 4.

Hope this helps.

---

### Post by coldReactive on 2009-11-15
> **Jon Monreal said:**
> I'm not certain that this is what you want, but you could right-click on the workspace switcher and select "Preferences". One there, change "Number of workspaces" to 4.

Hope this helps.

Gnome-Shell doesn't use gnome panel, no precious applets to save me. :(

---

### Post by Jon Monreal on 2009-11-15
> **coldReactive said:**
> Gnome-Shell doesn't use gnome panel, no precious applets to save me. :(

Ah, must be blind.

Try this: open a terminal and type "/usr/bin/gconf-editor" and press "enter". In the Configuration Editor, click the triangle next to "apps" then the one next to "metacity", click on "general", and find "num_workspaces". Right click on this, and click "Edit Key", and change the value to 4.

Always be careful when editing configuration settings.

---

### Post by coldReactive on 2009-11-15
> **Jon Monreal said:**
> Ah, must be blind.

Try this: open a terminal and type "/usr/bin/gconf-editor" and press "enter". In the Configuration Editor, click the triangle next to "apps" then the one next to "metacity", click on "general", and find "num_workspaces". Right click on this, and click "Edit Key", and change the value to 4.

Always be careful when editing configuration settings.

Didn't work, gnome shell still starts with only one workspace.

---

### Post by Jon Monreal on 2009-11-15
> **coldReactive said:**
> Didn't work, gnome shell still starts with only one workspace.

That's disappointing. You could try Edit -> Find and typing in "workspace" to see if you have any options that I don't related to Gnome-Shell.

EDIT: If you try this, remember to check "Search also in key names".

---

### Post by coldReactive on 2009-11-15
> **Jon Monreal said:**
> That's disappointing. You could try Edit -> Find and typing in "workspace" to see if you have any options that I don't related to Gnome-Shell.

It's sad, that didn't show anything either in relation to gnome-shell, sadly. :(

Looks like I'm going to KDE or xfce (more to xfce sadly, as I really dislike KDE.) In the future, as by 10.10, we'll have gnome-shell.

---

### Post by Jon Monreal on 2009-11-15
> **coldReactive said:**
> It's sad, that didn't show anything either in relation to gnome-shell, sadly. :(

Looks like I'm going to KDE or xfce (more to xfce sadly, as I really dislike KDE.) In the future, as by 10.10, we'll have gnome-shell.

Well, Gnome-Shell looks quite promising, but in its current state I wouldn't look at it for day-to-day use. Especially if there's no way to do such important things as changing the default number of workspaces.

Perhaps you should try Ctrl+Alt+Right Arrow just to see if there are more workspaces but they don't appear to be there.

---

### Post by coldReactive on 2009-11-15
> **Jon Monreal said:**
> Perhaps you should try Ctrl+Alt+Right Arrow just to see if there are more workspaces but they don't appear to be there.

No, that doesn't work. You first have to add workspaces to be able to change workspaces, sadly.

---

### Post by Jon Monreal on 2009-11-15
Oh well. I bet this won't be a problem is soon as applets are out for Gnome-Shell.

---

### Post by coldReactive on 2009-11-15
> **Jon Monreal said:**
> Oh well. I bet this won't be a problem is soon as applets are out for Gnome-Shell.

There won't be a global menu applet due to the active-window-name applet already in gnome-shell.

You can't even move any of the applets around, right-click doesn't work ANYWHERE in gnome-shell except for on the system tray, it's very frustrating!

---

### Post by Jon Monreal on 2009-11-15
> **coldReactive said:**
> There won't be a global menu applet due to the active-window-name applet already in gnome-shell.

You can't even move any of the applets around, right-click doesn't work ANYWHERE in gnome-shell except for on the system tray, it's very frustrating!

I think I'm going to have to give it a try just to see the state it's in, then.

I know it's supposed to be more application-centric and utilize workspaces to greater potential, but what sounds good on paper isn't always good in implementation.

---

### Post by moore.bryan on 2010-02-21
If anyone is still checking-out this thread, the solution is painfully easy. When you launch the GnomeShell activities window (the "Windows" key or by traveling to the top-left with your mouse), you'll see small plus and minus boxes in the bottom-right; that's where you add the number of workspaces you'd like GnomeShell to use. On the bottom-left, you'll see a place where you can choose to either slide through the workspaces or show all of them at one time.

I, too, am a four-workspace kinda guy.
:-)

---

