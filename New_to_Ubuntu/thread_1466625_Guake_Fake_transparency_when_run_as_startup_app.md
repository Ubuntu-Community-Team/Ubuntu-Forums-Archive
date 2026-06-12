---
title: "Guake: Fake transparency when run as startup app"
date: 2010-04-30
forum: New to Ubuntu
---

### Post by peculiar penguin on 2010-04-30
Installed Guake terminal and activated its entry in System/Preferences/Startup Applications to make it autostart on login. That works, but I get only fake transparency (just the desktop wallpaper, no windows) that way. Exit Guake and restart it manually, and I get proper transparency including windows.

Clean Lucid install, ATI Radeon X1250 IGP (radeon.modeset=0), Visual Effects set to "Normal".

Any ideas? :confused:

---

### Post by Michael Knap on 2010-04-30
Same here with nVidia and compiz

---

### Post by peculiar penguin on 2010-05-05
Looks like Guake is run too early, when Compiz isn't completely loaded or something.

Workaround: A really trivial startup script that sleeps a couple of seconds and then launches Guake.

---

### Post by ankspo71 on 2010-05-05
I agree about possibly needing a script. I never used guake before, but here's a sample script I use for other things that should help.

```
#!/bin/bash
sleep 30 && guake ;
```
save that as autostart-guake.sh 
then make a start up application entry for:
**sh /path-to-script/autostart-guake.sh**
I hope that helps.

---

### Post by peculiar penguin on 2010-05-05
Exactly, but at least in my case 5 seconds are enough for this.

---

### Post by Ice_l3lade on 2010-07-05
You don't need to create an entire script.
You can also just go to the startup applications menu, select the entry for Guake and change the command from "guake" to "sleep 5 && guake" and it should work. :)

EDIT:
Ah, maybe I should have tested before posting. Apparently you DO need a seperate helper script. Please disregard my post.

---

### Post by ChrisMP1 on 2010-07-16
No helper script needed. Just:
bash -c 'sleep 5s; guake'

---

### Post by perturbo on 2010-07-31
> **ChrisMP1 said:**
> No helper script needed. Just:
bash -c 'sleep 5s; guake'

This worked perfectly for me. Thanks!

---

### Post by pterosky on 2010-08-11
Perfect, thanks! Audacious wouldn't start up in 10.04, this fixed it:
```
bash -c 'sleep 5; audacious'
```

---

### Post by lrkwz on 2011-01-26
I had the same problem while "Visual effects" was set to "None" (metacity), setting to "Normal" fixed it (compiz is enabled at this point).

I remembered WHY I disabled compiz if favor of metacity! Using compiz with my nvidia geforge the windows decorator behave badly: window title and borders randomly do not appear. And guake itself sometimes is completely not drawn.

I solved both problems [enabling composting in metacity]("https://help.ubuntu.com/community/Metacity#General%20Settings").

---

