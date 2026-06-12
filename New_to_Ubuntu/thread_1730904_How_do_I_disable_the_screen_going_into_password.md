---
title: "How do I disable the screen going into password?"
date: 2011-04-16
forum: New to Ubuntu
---

### Post by papuccino1 on 2011-04-16
I have Ubuntu 10 installed on a VM on VMWare.

After I leave it on for a bit the screen goes black and when I move the mouse I have to input my password to go back into the environment.

How do I disable this? I want it to remain active ALWAYS.

Thanks! :)

---

### Post by TeoBigusGeekus on 2011-04-16
Go to Administration>Preferences>Screensaver
Uncheck the Ask for Password After Resuming (or something like that) option.

---

### Post by richaoj on 2011-04-16
I do not think the screensaver thing is what's going on.  I would also check the power options by clicking the battery icon (or going to administration -> power options)  and look for the setting about putting the display to sleep.  I don't think the screensaver is activating.  The display is going to sleep, and then asking for the password when waking up.

So prevent the display from going to sleep, and then you can enable screensaver if you wish . . . . . without password.

---

### Post by wep940 on 2011-04-17
Both of you could be right depending on how the OP has their computer set up.  The OP should go to system/preferences/screen saver and set it to what they want - a blank screen if they so desire.  Then towards the bottom of the screen are 2 options - the one that says to lock when screen saver is active should be unchecked - you won't get asked for your password when you wake up the screen from either the power settings limit or the screen saver.

---

