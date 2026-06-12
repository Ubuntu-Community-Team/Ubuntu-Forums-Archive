---
title: "Sound and Dual Display Issues"
date: 2009-07-18
forum: New to Ubuntu
---

### Post by mikeypc2006 on 2009-07-18
I'm running Ubuntu 9.04 on my desktop.  I have a Creative Labs Sound Blaster Audigy 4 Sound Card and 256MB nVIDIA GeForce 7600 GS graphics card.  I am unable to get any sound unless I turn my speakers up to full volume and only then, it is very quiet.  I have tried doing what this thread suggests in the first post [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449) and turned everything I can see up to full volume, but the sound still comes out very quietly.

The other issue I have is with dual screen support.  How do I tell the nVIDA control panel to save my dual screen settings?  The save function refuses to save the settings to a file anywhere.  Every time I start Ubuntu, I'm back to a single screen unless I play with the nVIDA control panel.  Also, when I apply the dual screen settings, despite me specifying the monitor I want as the primary display, the application launch bar and the task bar of running programs are very unpredictable as to where they'll end up, they aren't always both necessarily on the primary screen!  How do I tell Ubuntu to remember my dual screen settings and always have the application launcher and task bar on the primary screen?

In contrast, sound and dual screen support work no problems under Windows 7 RC!

---

### Post by swoll1980 on 2009-07-19
> **mikeypc2006 said:**
> I'm running Ubuntu 9.04 on my desktop.  I have a Creative Labs Sound Blaster Audigy 4 Sound Card and 256MB nVIDIA GeForce 7600 GS graphics card.  I am unable to get any sound unless I turn my speakers up to full volume and only then, it is very quiet.  I have tried doing what this thread suggests in the first post [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449) and turned everything I can see up to full volume, but the sound still comes out very quietly.

The other issue I have is with dual screen support.  How do I tell the nVIDA control panel to save my dual screen settings?  The save function refuses to save the settings to a file anywhere.  Every time I start Ubuntu, I'm back to a single screen unless I play with the nVIDA control panel.  Also, when I apply the dual screen settings, despite me specifying the monitor I want as the primary display, the application launch bar and the task bar of running programs are very unpredictable as to where they'll end up, they aren't always both necessarily on the primary screen!  How do I tell Ubuntu to remember my dual screen settings and always have the application launcher and task bar on the primary screen?

In contrast, sound and dual screen support work no problems under Windows 7 RC!

I don't know about your sound issue, but if you open nvidia settings with root privileges you will be able to save the file.
```
gksu nvidia-settings 
```
I change it in the menu too. right click your "start button" go to edit menu, find nvida settings, hit properties, then change the command by putting the gksu in front of it.

---

### Post by mikeypc2006 on 2009-07-19
Thanks, that is much appreciated, I will try it later! :)

---

### Post by Conzo on 2009-07-29
> **swoll1980 said:**
> I don't know about your sound issue, but if you open nvidia settings with root privileges you will be able to save the file.
```
gksu nvidia-settings 
```I change it in the menu too. right click your "start button" go to edit menu, find nvida settings, hit properties, then change the command by putting the gksu in front of it.


Thank you for posting this, I was Having this problem also ,
Work great   , i was trying sudo gedit xconf.file  it was saving but on the restart my Display drives where not working !


Thanks all for you Time and wisdom! 
Conzo

---

