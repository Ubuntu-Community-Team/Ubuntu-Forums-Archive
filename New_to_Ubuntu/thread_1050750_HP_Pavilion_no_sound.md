---
title: "HP Pavilion no sound"
date: 2009-01-26
forum: New to Ubuntu
---

### Post by tjlane on 2009-01-26
Hi all, and thanks for reading.

I'm running Ubuntu 8.10 on a brand-new HP Pavilion dv4 1225dx. Everything works fine, except for the fact that I have zero sound. It read the card just fine at first, just wouldn't output anything.

However, after downloading and installing the latest ALSA drivers, it can't even find the card.

Oh, the card, I should mention, is an SBx00 ATI Azalia (Intel HDA).

Does anyone know what I should do?

Or at least, how I might get rid of the even-more-problematic driver update?

Thanks again!

---

### Post by diablo75 on 2009-01-26
Try this:

Double-click on the speaker icon in the upper panel by the clock.

Once that opens your volume panel, click Preferences.

Check off all the devices that look like they could potentially produce sound (e.g., "Front", "Front PCM", "Surround", etc).  Check the ALL off if you want and close it.

The volume panel with expand with new levers.  Play some music in the background and start playing with those levers.  I've found on these intel HDA's that I often have to turn up the Surround PCM or something like that before sound will come out of the front speakers.  Kind of strange, but it works.

---

### Post by tjlane on 2009-01-26
Thank you for the response- at this point, though, I am unable to access any volume control whatsoever. Clicking the speaker icon only brings up an error message reading: No volume control Gstreamer plugins or devices found.

---

### Post by tjlane on 2009-01-26
B-b-b-bump!

---

### Post by Mark Phelps on 2009-01-27
I had similar problems until ALSA finally included a driver for my sound card.  Seems that the brand-new sound chips take a while to make it into the ALSA driver set.

Suggest you check out the Open Sound System website for drivers.  I had to install their drivers until ALSA caught up.  Link to a list of supported devices is below:

[http://manuals.opensound.com/devlists/Linux.html]("http://manuals.opensound.com/devlists/Linux.html")

---

### Post by tjlane on 2009-01-28
Thank you very much, I'll give this a shot!

---

### Post by tjlane on 2009-01-31
Well, it didn't work. I gave it a valiant effort, but alas, I am bested.

---

### Post by mal2104 on 2009-02-13
Somewhat solved in this thread

[http://ubuntuforums.org/showthread.php?t=1042840&highlight=hp+dv4-1225dx](http://ubuntuforums.org/showthread.php?t=1042840&highlight=hp+dv4-1225dx)

Sound quality isn't a good as could be, but you get some.

---

