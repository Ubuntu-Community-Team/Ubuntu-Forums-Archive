---
title: "Missing Task bar and virtual windows"
date: 2010-03-11
forum: New to Ubuntu
---

### Post by ubu newb on 2010-03-11
[FONT=Arial][SIZE=2][COLOR=Navy]Sorry if my terminology is wrong.  Ubuntu 9.10 installed from Windows using wubi.

[/COLOR][/SIZE][/FONT]    [FONT=Arial][SIZE=2][COLOR=Navy]Upon first booting into ubuntu I can't see either  task bar, virtual or main.  I can move between windows by alt-tab but can't click on a minimize window to bring it up.  I have no access to applets, places or system or to be able to restart, shut down or even manage wireless connection.[/COLOR][/SIZE][/FONT]


[FONT=Arial][SIZE=2][COLOR=Navy]I did file a bug for this but is there something I can try to get them back or do I need to do the dreaded uninstall and reinstall from Windows?
[/COLOR][/SIZE][/FONT]

---

### Post by undecim on 2010-03-11
Have you tried adjusting your monitor?

Often times when I run the live CD on someone else's computer, I have to press the monitor's auto-adjust button, otherwise the task bar is off-screen.

---

### Post by Temposs on 2010-03-11
Well, I see two possible problems here, and I'm not sure which it is.

1) Your resolution is messed up, so that the Ubuntu desktop is extending off of your physical screen, hiding the panels.

2) For some reason, the panels got deleted. This is the easier problem to fix, of course.

To find out which one it is that is happening, when you move your mouse to the top of the Ubuntu screen, can the mouse go off the screen? How about when you go to the left side of the screen?

---

### Post by ubu newb on 2010-03-11
> **undecim said:**
> Have you tried adjusting your monitor?

Often times when I run the live CD on someone else's computer, I have to press the monitor's auto-adjust button, otherwise the task bar is off-screen.


Not a monitor issue.  I forgot to mention it's on a Toshiba laptop.   I also don't have auto hide on.

---

### Post by undecim on 2010-03-11
> **ubu newb said:**
> Not a monitor issue.  I forgot to mention it's on a Toshiba laptop.   I also don't have auto hide on.

Then it's either Temposs's second idea, or there is a problem with gnome-panel.

Does pressing ALT+F2 do anything?

---

### Post by ubu newb on 2010-03-11
No, hitting Alt-F12 does nothing.

Moving my mouse to the bottom and right side goes off the screen.   I did move the task bar to the bottom of the screen last time it worked.

---

### Post by Temposs on 2010-03-11
undecim said Alt+F2, not Alt+F12. Anyway, that doesn't matter much.

It seems like your panels are just gone. What I'd like you to do is press Ctrl+Alt+F1. This will take you to a black screen and let you login. It won't show your password as you type it, but it's still putting in your password. Then it will give you the command line. I'd like you to type in this command:

```
rm -rf .gconf .gnome .gnome2
```

Ideally it will give you no reply back, it will just give you the prompt again. Then restart Ubuntu by doing this command:

```
sudo shutdown -r now
```

See if that brings up your panels when it restarts.

---

### Post by ubu newb on 2010-03-11
Thanks Tempboss and undecim all working again. :)

---

