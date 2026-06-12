---
title: "Global $NOTIFY variable"
date: 2011-03-02
forum: New to Ubuntu
---

### Post by Blutkoete on 2011-03-02
Hello!

Is there a global variable or a command to notify the user?

I found x-www-browser for the browser while googling, but that actually starts rekonq on my Kubuntu and not my chosen default browser.

My problem is not with the browser, but with a way to notify the user via his main notification daemon. I wrote a MATLAB script once to to that, but it only works with Ubuntu (Gnome), but I'd like it to work with all Ubuntu variants (at least Kubuntu and Ubuntu) as I'm using both.

Is there something like $NOTIFY which refers to the standard notification system which I could read to find out what command to call?

Thank you,

Blutkoete

---

### Post by Mariane on 2011-03-02
What are you trying to notify about? 

Mariane

---

### Post by Blutkoete on 2011-03-02
I want my MATLAB simulations to send me desktop notifications if they've reached a certain simulation step.

The script works fine with Ubuntu, but not with Kubuntu as that appears to use a different notification system.

In Ubuntu, my script simply sends a *system('notify-send TEXT')* command which isn't installed on Kubuntu. I could simply install it, but there is already some notification system and I don't want to replace it.

But all the other programs (Firefox, etc.) seem to know how to send notifications, whether on Kubuntu or Ubuntu, so I thought there is some global setting that I can look at to determine which command sends desktop notifications in which version.

---

### Post by gmargo on 2011-03-02
You can safely install the **libnotify-bin** package on Kubuntu, to get the **notify-send** command.  It won't replace anything, and it works fine.

---

### Post by Blutkoete on 2011-03-02
Thank you, I'll simply install & use that then.

---

