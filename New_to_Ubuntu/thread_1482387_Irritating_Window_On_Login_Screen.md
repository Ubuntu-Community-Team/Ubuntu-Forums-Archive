---
title: "Irritating Window On Login Screen"
date: 2010-05-13
forum: New to Ubuntu
---

### Post by orphanlast on 2010-05-13
I accidentally left my computer on when I had the "appearance" window up (Which is accessed through SYSTEM>PREFERENCES>APPEARANCE). One of my relatives was staying in the house and noticed this, didn't know how to turn off the computer because it's not Windows and turned the computer off while on the login screen.

Because of this, every time I restart my computer the APPEARANCE window appears on my login screen. 

Does anyone know of a way to stop that from happening? 

Thanks

:guitar:

---

### Post by bredman on 2010-05-13
Use the menu item System/Preferences/Startup Applications to see if this application is marked to start automatically.

---

### Post by orphanlast on 2010-05-13
Unfortunately it's not showing up as a startup file.

---

### Post by CharlesA on 2010-05-13
Stupid question, but are you able to login, close it and reboot?

---

### Post by theozzlives on 2010-05-13
> **orphanlast said:**
> I accidentally left my computer on when I had the "appearance" window up (Which is accessed through SYSTEM>PREFERENCES>APPEARANCE). One of my relatives was staying in the house and noticed this, didn't know how to turn off the computer because it's not Windows and turned the computer off while on the login screen.

Because of this, every time I restart my computer the APPEARANCE window appears on my login screen. 

Does anyone know of a way to stop that from happening? 

Thanks

:guitar:

That's interesting. First of all tell your friends to keep their grubby hands off your computer! Second, try logging on, bring up appearance and close it, then reboot the right way.

---

### Post by orphanlast on 2010-05-14
> **CharlesA said:**
> Stupid question, but are you able to login,  close it and reboot?

Oh yeah, that's all really easy.

> **theozzlives said:**
> That's interesting. First of all tell your friends to keep their grubby hands off your computer! 

Yeah, it's better to have your computer running all day rather than just pressing the power button.

>  Second, try logging on, bring up appearance and close it, then reboot the right way.

Sweet, I'll give that a try tomorrow morning.

---

### Post by orphanlast on 2010-05-14
Turning the computer on, getting rid of the attributes window and shutting it down didn't really do it.

---

### Post by Sealbhach on 2010-05-14
> **orphanlast said:**
> Turning the computer on, getting rid of the attributes window and shutting it down didn't really do it.

This may be pointless, but try flushing out swap:

sudo swapoff -a
sudo swapon -a

---

### Post by orphanlast on 2010-05-15
nope. That didn't seem to work.

I'm starting to have another problem. (Not sure if it's relivant). But sometimes the minimize, maximise, and close buttons won't even show up at the top of a window. Usually restarting the computer fixes that little problem. It's doing it less and less. I did and update on my system and the last time I restarted my computer (I did it about five times this morning) and after the fourth, it rebooted and "checked with errors with my hardware" and then rebooted itself again and when my desktop came up, everything was fine.

---

### Post by rhedman2 on 2010-05-24
I believe what you're looking for is..

[COLOR=#C20CB9]**sudo**[/COLOR] [COLOR=#C20CB9]**unlink**[/COLOR] [COLOR=#000000]**/**[/COLOR]usr[COLOR=#000000]**/**[/COLOR]share[COLOR=#000000]**/**[/COLOR]gdm[COLOR=#000000]**/**[/COLOR]autostart[COLOR=#000000]**/**[/COLOR]LoginWindow[COLOR=#000000]**/**[/COLOR]gnome-appearance-properties.desktop

---

