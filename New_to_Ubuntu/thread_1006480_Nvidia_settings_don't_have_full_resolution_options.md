---
title: "Nvidia settings don't have full resolution options"
date: 2008-12-09
forum: New to Ubuntu
---

### Post by joonga on 2008-12-09
Greetings.

Geez, where to start. Just installed xubuntu 8.10 on my old x86 intel box. I also have an older Nvidia grfx card (GeForce3 Ti200), but it worked quite well on a former windows xp box. After installing the suggested drivers (v96.03.49), I discovered that there are no higher resolution options available to choose from, from the settings window. In other words, I can't work in 1280X1024 res, as there are only the auto, 640x480, 230x240 options to choose from and available from the x server display config. I wonder where I might've gone wrong? As a note, after login in for the 1st time, before installing the Nvidia drvs, the resolution was quite 'normal', though set to a seemingly much higher res than 1280x1024. Then, the next time I rebooted and logged back in, the res was set to the default 640x480 res.? So, maybe the best thing for me would be to go back to whatever drvs were installed at the outset, however I don't know though. Any thoughts or areas I should explore.

Many thanks in advance.
joonga.
:confused:

---

### Post by w4ett on 2008-12-09
To get the new setting to save you must be in superuser mode.  In the terminal:

> gksu nvidia-settings

---

### Post by joonga on 2008-12-09
will try W4ett.

thx.
Jnga

---

### Post by joonga on 2008-12-09
I just tried via the terminal cmd line. Though the Nvidia settings window does open, the shell display a list of errors to this effect:

ERROR: Cannot open display 'valis:0.0'.


ERROR: Unable to assign attribute DigitalVibrance specified on line 19 of
       configuration file '/home/pierre/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute SyncToVBlank specified on line 20 of
       configuration file '/home/pierre/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute AllowFlipping specified on line 21 of
       configuration file '/home/pierre/.nvidia-settings-rc' (no Display
       connection).
______________________

and so on so forth for dozen more attributes. Again, however, there are still only a few basic resolution options available from the x server config panel.

Anyway, your help is very much appreciated.
All the best.
J.

---

### Post by joonga on 2008-12-10
Greetings.

I've tried the prescribed workaround by w4ett, however without any success. As I was experiencing other issues as well in xubuneez, I decided to re-install xubuntu yesterday. And, as an experiment, I also decided not to install the Nvidia drvs, with the result that the desktop res. has remained 'normal' up until now, plus I can choose from the standard meat-'N'-patatoes Display resolutions from the setup manager-Display controls. Perhaps - in my case - the best thing to do is to leave things as there are display-wise. 

Again, thank you for your time and feedback.
Regards.
Joonga.

---

### Post by philinux on 2008-12-10
Under Sys>Admin>Hardware drivers is any driver offered?

---

### Post by joonga on 2008-12-10
Thanks Philinux.

Nothing appears in the Hardware drvs window: "no proprietary drivers are in use on this system". Though, as I mentioned already, I encountered the same issue yesterday, and after seeing that no drvs were installed, I went ahead and installed the recommended Nvidia drvs, and that's when my display problems began.

J.

---

### Post by LowSky on 2008-12-10
for such an old card you really should only be using the legacy drivers if needed

---

### Post by joonga on 2008-12-10
I agree LowSky. I'm happy now the way it is, as the display looks and performs normally... knock on my monitor

---

### Post by joonga on 2008-12-13
):P
Please close/resolved this thread, as my display resolution issue is A-okay.

Many thanks to all.
Cheers.
Joonga

---

