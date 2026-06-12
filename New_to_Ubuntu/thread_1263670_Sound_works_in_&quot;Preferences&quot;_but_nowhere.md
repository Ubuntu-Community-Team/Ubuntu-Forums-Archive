---
title: "Sound works in &quot;Preferences&quot; but nowhere else."
date: 2009-09-11
forum: New to Ubuntu
---

### Post by Infammo on 2009-09-11
I can only hear sound in ubuntu when I'm doing the "testing pipeline" in sound prefences.  But no sound is coming from anywhere else.

The sound in alsa and volume control is turned all the way up and nothing is muted.

---

### Post by SunnyRabbiera on 2009-09-11
Strange, if you are able to hear the test sound then you should be able to hear something.
Did you try changing your sound server?
It might be Pulseaudio

---

### Post by Infammo on 2009-09-11
Heh, sorry could you clarify that?  I just converted from windows, so I'm totally new at this.  It took all night googling just to get my sounds card recognized and configure it with alsa.  Before now I didn't even get sound in "testing pipeline."

Thanks for the quick reply anyway.

---

### Post by fluxbuntu on 2009-09-11
Some audio players let you select the sound driver to use. Check your preferences in your player to make sure it is using alsa. Run alsa mixer and make sure that Master and PCM are turned up also. If those don't work then run alsaconf to reload the driver. Are you not hearing the audio player or system sounds or what?

---

### Post by Infammo on 2009-09-11
I don't have any audio saved so I go to a random video on the internet to test the sound.  The volume's turned up on those.  If there are any system sounds from clicking or whatnot then I'm not hearing those either.

I don't know what alsaconf is.

---

### Post by Infammo on 2009-09-11
Update: I tried restarted Ubuntu, and now the sound doesn't work even in preferences, and I can't open alsamixer.  When I type it into the terminal it says "no such file or directory."

"sudo apt-get install alsamixer" Gives me the message "couldn't find package alsamixer."

---

### Post by fluxbuntu on 2009-09-11
A random video could be flash or anything causing the issue. Try this link for testing audio and plugins. 
[http://fredrik.hubbe.net/plugger/test.html](http://fredrik.hubbe.net/plugger/test.html)
This will let you either play the test file within a browser or download it and play from your computer. alsaconf is a utility ran from the command line to configure alsa and reload the drivers.

---

### Post by fluxbuntu on 2009-09-11
apt-cache search alsamixer shows 3 possibles to install. alsa-utils alsamixergui and gnome-alsamixer. Do sudo apt-get update and then sudo apt-get install alsa-utils alsamixergui or gnome-alsamixer if your using the default gnome install. You don't need the gui and gnome. I had this problem before when using gnome and had to run alsaconf for some reason to load the sound driver. I think it has been omitted from alsa-utils now and may require to googling to find but it always worked.

---

### Post by Infammo on 2009-09-11
Can't hear anything, but now sound in my system is completely in the tank.

aplay -l gives me "no soundcards found..."

Clearly something went horribly wrong that last reboot.  Back to google I guess. :(

---

### Post by Infammo on 2009-09-11
> **fluxbuntu said:**
> apt-cache search alsamixer shows 3 possibles to install. alsa-utils alsamixergui and gnome-alsamixer. Do sudo apt-get update and then sudo apt-get install alsa-utils alsamixergui or gnome-alsamixer if your using the default gnome install.

I installed both of those but it still says "no such file or directory" when I try to start alsamixer.

---

### Post by fluxbuntu on 2009-09-11
You can try lshw to see if the system even sees a sound card. I wish I could offer more advice but I'm tapped out as far as alsa goes. If you can find alsaconf though I think it will resolve this for you. Luck.

---

