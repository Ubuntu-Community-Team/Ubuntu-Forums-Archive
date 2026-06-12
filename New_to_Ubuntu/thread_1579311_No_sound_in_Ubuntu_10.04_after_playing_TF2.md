---
title: "No sound in Ubuntu 10.04 after playing TF2"
date: 2010-09-21
forum: New to Ubuntu
---

### Post by Pyrohyper on 2010-09-21
Hi.
I'm using Ubuntu 10.04 on my Acer laptop 5520g.
I was having problems before but i have just simply solved a problem with:
```
sudo aptitude install linux-ubuntu-modules-`uname -r` linux-generic
```
and everything is normal, i mean i have my sound back after restart.
But now i was playing team fortress 2 on my playonlinux a than my sound was gone.
I tried to do sudo again and again (after every update i restart my laptop).
Please help me.I can't live without music

---

### Post by lkjoel on 2010-09-21
> **Pyrohyper said:**
> Hi.
I'm using Ubuntu 10.04 on my Acer laptop 5520g.
I was having problems before but i have just simply solved a problem with:
```
sudo aptitude install linux-ubuntu-modules-`uname -r` linux-generic
```
and everything is normal, i mean i have my sound back after restart.
But now i was playing team fortress 2 on my playonlinux a than my sound was gone.
I tried to do sudo again and again (after every update i restart my laptop).
Please help me.I can't live without music
Try Fix your sound! in my signature.

---

### Post by Pyrohyper on 2010-09-21
Fix your sound! didn't work for me :(

---

### Post by bradleypariah on 2010-09-21
This is a long-shot, but MythTV often locks me out of sound even after it's closed.
When it does, I go to System > Administration > System Monitor and look at the Processes tab for anything that looks like it might be taking control of my audio drivers.  If this is the case, end that fishy process and sound should come right back.
Hopefully that helps, I don't have nay other suggestions.  I've only been a Linux user for a year or two.

---

### Post by Crazedpsyc on 2010-09-21
have you tried rebooting? I know that would be annoying to have to do it each time, but... Also install padevchooser and run it from apps>S&V>PulseAudio Device Chooser. then click on it's applet and select volume control. go to the playback tab. look for team fortress 2 or something similar, and if you see it there right click on it and select Terminate Playback

---

### Post by bradleypariah on 2010-09-21
Woah!  That's a cool one.  This thread wasn't even mine and I learned something.  :-D

---

### Post by Pyrohyper on 2010-09-21
> **Crazedpsyc said:**
> have you tried rebooting? I know that would be annoying to have to do it each time, but... Also install padevchooser and run it from apps>S&V>PulseAudio Device Chooser. then click on it's applet and select volume control. go to the playback tab. look for team fortress 2 or something similar, and if you see it there right click on it and select Terminate Playback

I rebooted my system like thousand times and still nothing. In System monitor doesn't show me anything that is using my sound card (there is just chrome browser opened). I reinstalled Alsa and Pulse and still nothing.
In pulse doesn't even detect my sound card :(

---

### Post by bradleypariah on 2010-09-21
Do you have GNOME ALSA Mixer installed?  It might expose a muted output.
Have you gone the easy route? - Have you checked in 
System > Preferences > Sound and ensured your outputs are still assigned correctly?

---

### Post by Pyrohyper on 2010-09-21
> **bradleypariah said:**
> Do you have GNOME ALSA Mixer installed?  It might expose a muted output.
Have you gone the easy route? - Have you checked in 
System > Preferences > Sound and ensured your outputs are still assigned correctly?

I have it installed.But when i start up Alsa mixer it does'n show me anyhing.Pulse doesn't show me my output, i mean my sound card

---

