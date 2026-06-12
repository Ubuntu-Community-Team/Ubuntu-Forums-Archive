---
title: "Restoring ~/.profile?"
date: 2009-07-03
forum: New to Ubuntu
---

### Post by rawny on 2009-07-03
Hi there,

I'm fairly new to Ubuntu and I have, rather foolishly, managed to overwrite my ~/.profile file with my settings from the CompizConfig Settings Manager #-o

I'm running Ubuntu 9.04 (64-bit) and just to clarify, as far as I know I don't have a backup of the ~/.profile file from before I overwrote it.

I'm unable to start a "normal GNOME session"(?) as I get:

"Your session only lasted less than 10 seconds..."

This is in the accompanying error log:
```
/etc/gdm/Xsession: Beginning session startup...
/home/rawny/.profile: 1: [firepaint]: not found
/home/rawny/.profile: 2: Syntax error: redirecton unexpected
```This matches up with the contents of my ~/.profile file which begins:
```
[firepaint]
as_clear_button = <Shift><Super>Button2
```(I'm currently in a failsafe GNOME session.)

Anyway, my questions are:
- Is there a way to restore my ~/.profile file to how it is supposed to be (i.e. a command)?
- Is there somewhere I could get a copy of how the file is supposed to look and replace it with that?
- If I were to delete the file, would Ubuntu be able to restore it upon restarting?

I think that's pretty much everything, any help would be much appreciated, thanks!
Rawny ^^

---

### Post by btmiller on 2009-07-03
There's no way to get your ~/.profile back if you didn't back it up. However, you can copy the system default profule from /etc/skel into your home directory.

---

### Post by rawny on 2009-07-03
Yeah fair enough, I copied the default one from /etc/skel and logged in fine, thanks a lot! :-)

---

