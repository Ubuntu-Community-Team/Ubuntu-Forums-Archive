---
title: "I don't want a password"
date: 2010-08-29
forum: New to Ubuntu
---

### Post by robmccolley on 2010-08-29
Ubuntu prompts me for a password after 5 minutes of inactivity. I don't like that.

I don't think I can change it. Can I?

Here's the problem with a pedantic password:

In the middle of the night, when listening to an audiobook; I don't want to sit up in bed, find the keyboard, turn on the light, and type 4 to 6 numbers and letters simply to hear Nigel Planer instead of Stephen Briggs.

I looked around various fora, and most "password" discussions involve keyring and root problems. I don't care about that. I don't want any password prompt -- ever.

I doubt anyone will sneak into my room at night to use my computer. But if they do, I don't want them to have to wake me up to ask for my password.:confused::confused:

---

### Post by christophski on 2010-08-29
To stop the password prompt after the computer is idle, go into System -> Preferences -> Screensaver and uncheck "Lock Screen When Screensaver is Active"
Hope that helps

---

### Post by robmccolley on 2010-08-29
I'll give it a whirl. Thanks.

---

### Post by aysiu on 2010-08-29
Yes, there are settings to turn off the password prompt for screensaver or for resuming from sleep or hibernate. If you can't find them in the regular graphical user interface (GUI), press Alt-F2 and paste in ```
gconf-editor
``` and you can go to Apps > gnome-power-manager > lock or Apps > gnome-screensaver

Let us know if you run into any problems.

---

