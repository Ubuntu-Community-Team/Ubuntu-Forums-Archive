---
title: "Mouse cursor disappears after 2 seconds?"
date: 2010-08-06
forum: New to Ubuntu
---

### Post by D1Knight on 2010-08-06
Hello all. I have noticed that for sometime now (do not know which update caused the change), my mouse cursor disappears after 2 seconds on screen. I do not like this, some may like it.

Also, the mouse cursor style does not stay consistent "flips back and forth"(in window-default style, outside window-preferred style). This I am sure annoys a lot of people, does not look good.

---

### Post by iShurtugal on 2010-08-06
Can you duplicate the problem (can you make it happen on command/does it happen every time)?  if so, file a bug report with gnome [here]("https://bugzilla.gnome.org/")
and they'll try to fix it.  It will tell you what to do there.

---

### Post by D1Knight on 2010-08-06
> **iShurtugal said:**
> Can you duplicate the problem (can you make it happen on command/does it happen every time)?  if so, file a bug report with gnome [here]("https://bugzilla.gnome.org/")
and they'll try to fix it.  It will tell you what to do there.

Thanks for your response.:) It happens every time. I had recently tried an installation of openSUSE 11.3 GNOME, cursor was just fine!?

---

### Post by Malac on 2010-08-14
I too have noticed this behaviour recently. 
I suspect it is a setting that has been changed and should be in mouse preferences but isn't. 
It should be reported as a bug really as it is unconfigurable IMHO. 
If anyone finds a fix please post it. 
Thanks.

---

### Post by Malac on 2010-08-21
Okay I seem to have tracked this down.
As part of Ubuntu an app called unclutter is installed by default now, this is responsible for the mouse hiding behaviour.
You can stop it by issuing :```
 sudo apt-get remove unclutter
```at the command prompt or uninstall via synaptic.

If you don't want to remove it you can alter whether it starts or it's startup options by altering the file /etc/default/unclutter.
man unclutter lists the options and what they do.

Hope this helps.

p.s. please mark this thread as solved, thanks.

---

### Post by D1Knight on 2010-08-28
> **Malac said:**
> Okay I seem to have tracked this down.
As part of Ubuntu an app called unclutter is installed by default now, this is responsible for the mouse hiding behaviour.
You can stop it by issuing :```
 sudo apt-get remove unclutter
```at the command prompt or uninstall via synaptic.

If you don't want to remove it you can alter whether it starts or it's startup options by altering the file /etc/default/unclutter.
man unclutter lists the options and what they do.

Hope this helps.

p.s. please mark this thread as solved, thanks.
Malac, I thank you kindly for you response and help.:)I shall give  it a go once I am back up and running Ubuntu 10.04 (that's another issue). Great advice. Have an excellent week.:D

---

### Post by Malac on 2010-08-30
> **D1Knight said:**
> Malac, I thank you kindly for you response and help.:)I shall give  it a go once I am back up and running Ubuntu 10.04 (that's another issue). Great advice. Have an excellent week.:D
You're welcome, good luck getting Ubuntu running again.:D

---

### Post by rodeopete on 2012-03-11
Thanks for this response... this has been driving me to distraction for ages!

---

