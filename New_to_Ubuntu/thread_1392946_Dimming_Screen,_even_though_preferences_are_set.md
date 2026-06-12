---
title: "Dimming Screen, even though preferences are set"
date: 2010-01-28
forum: New to Ubuntu
---

### Post by LadySapphira on 2010-01-28
Two problems. 

One - sometimes/often even though the icon in the top right indicates my laptop is charging the display/power saver setting will act as if they are in battery power.


Also, even though I have unchecked the boxes that say dim display when idle, it still dims!

Another annoyance - I watch movies in firefox, and every 10 minutes or so it minimizes the fullscreen and lowers the brightness within a minute.


What can I do to fix this?  I have changed settings in "display" and "power management"

Thanks:KS

---

### Post by shae on 2010-01-28
Do either of these problems occur in Windows, if you still use it?

---

### Post by LadySapphira on 2010-01-30
Windows XP is normal, it never happens there =)

---

### Post by warfacegod on 2010-01-31
Have you disabled your screensaver? I think by default screensaver just blanks the screen.

---

### Post by synapsys on 2010-01-31
System >> Preferences >> Screensaver

---

### Post by LadySapphira on 2010-02-01
I have my screensaver set to not come on, the screen still dims it's actually about every 5 minutes =)

Thank you so much for the replies, I hadn't double checked the screensaver at the time.

---

### Post by warfacegod on 2010-02-01
You might try poking around in the Configuration Editor. Power settings and whatnot.

---

### Post by es0x279e on 2010-08-04
Hi there,

I'm having the same (or at least similar) problem with an Acer 1825PTZ. I've tried both the power-manager and screensaver options (everything that might dim the screen disabled) and also I gconf-edited these programs to make sure they save these preferences.

Now, my findings:
[LIST]
[*]Though everything is disabled, there is still the option "power_management_delay" in the screensaver gconf-iguration that still sends some evil signal to powermanagement to dim the screen.
[*]This preference is a number of seconds of inactivity before the signal sending, exactly 30, the number of second before the screen dims.
[*]Key stroke prevents screensaver to send the signal, but **events on the touchpad don't**.  
[/LIST]

Disabling these options do not change a thing and everything is still messed. 1) I don't understand why the screen dims every 30 second even if I changed all that options. 2) I do not know why the key stroke change the inactivity state but movement in the touchpad don't.

Any ideas? Thanks!

Btw, I'm in a Acer 1825PTZ with Ubuntu 10.04, kernel 2.26.35-13 from the xorg-edgers (this is not the reason of these issues as I had them before upgrading into xorg-edgers).

---

### Post by bohica910 on 2010-12-07
Lenovo T400; Ubuntu 10.10; on AC power... screen dimming after 30 sec (or so)

Like the guys above, I'd set power management, screensaver etc to always on/no dim but the screen kept on dimming. 

Saw the msg about checking the screen saver so... System-prefs-screensaver
All looked fine, clicked the power management button and.... screen dimmed. V strange??? 

In power management the 'on AC power' settings were all OK but then I changed the 'on battery' settings. I unchecked the screen controls and hey presto... no more screen dimming on AC power

Maybe someone could take a look at the power mgmt processes?

---

