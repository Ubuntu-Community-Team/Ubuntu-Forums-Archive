---
title: "Lock screen not working in Karmic"
date: 2009-11-11
forum: New to Ubuntu
---

### Post by abhiroopb on 2009-11-11
Whether I use the keyboard short-cut (CTRL+ALT+L) or I click on the "Lock Screen" button in the applications menu, nothing seems to happen.

How do I get my screen to lock?

It worked fine in jaunty :S!

---

### Post by fedoraboy on 2009-11-11
Ok, I have a confession before I answer: I absolutely can't stand gnome-screensaver.  It's basically xscreensaver that has been dumbed down and (sometimes) broken.

One of the first things I always do with a new ubuntu install is:

```

sudo apt-get remove gnome-screensaver
sudo apt-get install xscreensaver

```

If there isn't a built-in lock, just "Add to panel" a custom application launcher with the command:
```

xscreensaver-command --lock

```

---

### Post by abhiroopb on 2009-11-11
Thanks for the help. I used the xscreensaver-command --lock and did gnome-screensave --lock and found that the screensaver process was not running. So, I started the process, added it to the startup applications and its fine now.

Thanks for the input!

---

### Post by smburu on 2010-01-07
Thanks for the info @fedoraboy, it was really bugging me, now its working.

This is what I ended up doing because I didn't really like how the xscreensaver dialog looked like(probably sounds vain...if so... oh well) 

I first removed the gnome-screensaver and then reinstalled it then I ran
[INDENT]```
gnome-screensaver
```[/INDENT]
to get it running again and everything worked fine.

Now looking back on it, I probably could have gotten away with just running that command.

Hopefully this helps someone.

Thanks

---

### Post by jejones3141 on 2010-01-21
I have sort of the opposite problem; when I lock the screen, sure enough, it locks, and the screensaver starts up... but moving the mouse or striking a key doesn't bring up anything indicating that the computer is paying attention, awaiting a password. Experimentation eventually showed that blindly typing the password worked.

Given the arrogant and high-handed way gnome-screensaver and its near total lack of per-user customizability was foisted on GNOME users, I halfway suspect that if I asked, I'd be told that behavior is not a bug, it's a feature.... but to be totally sure, I guess I will ask.

As I, too, utterly despise gnome-screensaver, I will follow fedoraboy's advice. Thanks.

---

### Post by Kensey on 2010-01-27
I'm having a similar issue, using xscreensaver:

* session-menu -> Lock Screen does nothing (I already symlinked /usr/bin/xscreensaver-command to /usr/bin/gnome-screensaver-command -- from what I read this isn't necessary any more but shouldn't hurt anything)

* When I lock manually with xscreensaver-command -lock, then go to unlock, the animation stops but no dialog appears.  Blindly typing the password unlocks it.

Is there a bug already filed, or should I file one?

---

### Post by Kensey on 2010-02-01
Turns out the locking is done by D-BUS and there was no .service file to tell D-BUS how to do it.

---

### Post by TheBellman on 2010-04-19
So, given that this is the **absolute beginner** forum, what do I need to do to fix it and get my Lock Screen working?

gnome-screensaver is already in the startup programs but it never kicks in.

Lock screen does not work from clicking on menu items not by pressing keyboard shortcut Ctrl+Alt+L

---

