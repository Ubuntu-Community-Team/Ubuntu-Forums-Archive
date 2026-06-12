---
title: "no sound"
date: 2011-01-14
forum: New to Ubuntu
---

### Post by Old Jimma on 2011-01-14
Hi Ubuntu Community:

I reinstalled 10.04 and it worked nicely, except for Amarok... it didn't have any sound.

I checked the forums for advice, and came across advice that recommended removing .pulse using rm -r .pulse

THen I had no sound at all!

Checked the forums again. Found the recommendation for the following code:
sudo apt-get purge pulseaudio gstreamer0.10-pulseaudio
sudo apt-get install alsa-base linux-sound-base alsa-utils
sudo apt-get install gnome-alsamixer

This restored sound. However, Firefox froze in a very weird way, so I reinstalled from synaptic, and rebooted.

No sound again.

When I go to: System > preferences > sound, I get a message that says: "Waiting for sound system to respond."

Can someone kindly help me restore sound?

Thanks!
Phil Smith
Duluth, GA

---

### Post by wjz on 2011-01-14
Sounds bad, maybe it could be your sound card?

---

### Post by Trandre on 2011-01-14
Try following this guide: [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

---

### Post by Old Jimma on 2011-01-14
Hi Trandre:

Thanks for your suggestion... it worked. I used:

sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils

followed by

sudo apt-get install linux-sound-base alsa-base alsa-utils

and everything was very cool.

I owe you a Coke, my friend! :D

Sincerely and with gratitude,
Phil Smith
Duluth, GA

---

### Post by moongya on 2011-03-13
i followed the above reply but to no avail. help

---

