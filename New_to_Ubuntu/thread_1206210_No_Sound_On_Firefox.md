---
title: "No Sound On Firefox"
date: 2009-07-06
forum: New to Ubuntu
---

### Post by wickedshiv on 2009-07-06
Okay, this is beyond a joke now. This is the third problem I've had in 3 weeks. This time it's Firefox. I watch Zero Punctuation and Unskippable religiously and today I went on to watch the new videos and there is no sound. At first I thought it might have been the site so I tried watching Halo vs Counterstrike on YouTube and that didn't work either. Then I went into preferences and tested the sound things and they worked fine. I'm getting sound from my music files and avi movies. What am I supposed to do??? Someone help please.

---

### Post by wojox on 2009-07-06
Update Flash

[http://support.mozilla.com/en-US/kb/Flash-based+videos+and+sound+do+not+play+correctly](http://support.mozilla.com/en-US/kb/Flash-based+videos+and+sound+do+not+play+correctly)

---

### Post by brianfactors on 2009-07-06
For me, the problem was pulse audio.

Once pulse was uninstalled, there wasn't any problems with flash's sound. ALSA works great.

Edit: As for the solutions offered by firefox, libflashsuppport has no installation candidate for me. And I'm already using flash 10. I had the same problems with skype, so I just removed Pulse.

Edit: Here's code:
```
sudo apt-get autoremove pulseaudio
```
Or you can search for it in synaptic. Which ever make you happy.

> < > Brian

---

### Post by wickedshiv on 2009-07-06
I tried both of your suggestions and neither of them worked. I still can't listen to any of the videos on escapist magazine. Are there any other ways I could fix it?

---

### Post by kansasnoob on 2009-07-06
First of all install gnome-alsamixer either from synaptic or go to terminal and run:

```
sudo apt-get install gnome-alsamixer
```

It'll then show in Sound & Video:

[ATTACH]120192[/ATTACH]

Lots of new toggles to look at!

Also check the flash video "block" volume. Sometimes if one video or audio is muted (or turned down) it'll stay that way even after a restart, etc.

Then look here:

[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

---

