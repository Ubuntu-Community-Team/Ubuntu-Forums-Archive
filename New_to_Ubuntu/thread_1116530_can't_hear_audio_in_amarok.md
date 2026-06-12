---
title: "can't hear audio in amarok"
date: 2009-04-05
forum: New to Ubuntu
---

### Post by Matt26 on 2009-04-05
for some reason when i try to play an audio file in my amarok player (latest version) i can't hear anything.  the player indicates the file is being played, but the message that normally pops up on my screen to indicate what song is playing doesn't appear, so i think it might be an issue with the amarok player.  i can hover over the audio file and play it fine in the file manager so i know my system sound is working fine.

i have tried restarting the amarok player- by closing it via the tray icon and killing the process in system monitor, but neither approach helped.

does anyone know of a way to fix this issue other than restarting the computer?

thanks.

---

### Post by GosthShadow on 2009-04-05
arch for audio drivers for your audio card
:lolflag:

---

### Post by Matt26 on 2009-04-05
> **GosthShadow said:**
> arch for audio drivers for your audio card
:lolflag:

my audio is working fine other than amarok playing audio files- i can hear system sounds and play audio files though the file manager as i already mentioned.

plus this issue just occurred all of a sudden- amarok was playing my music files fine earlier in the day, and then this happened.

---

### Post by outlikeashoe on 2009-04-05
Same problem here, it worked well until the last update, yesterday. I think it could be a phonon issue: using amarok before the update, a message appears showing "Phonon: falling back to default playback engine" or something similar, but the audio worked fine. After update this message doesn't appears but the audio won't work at all (only amarok).

---

### Post by outlikeashoe on 2009-04-05
I confirm that for me it's a phonon issue, I've downgraded from version 4:4.3.1 to 4:4.2.0 and it worked again. By the way, the message was: "Phonon. The audio playback device HDA Intel (ALC888 Analog) does not work. Falling back to default."

---

### Post by Matt26 on 2009-04-05
> **outlikeashoe said:**
> Same problem here, it worked well until the last update, yesterday. I think it could be a phonon issue: using amarok before the update, a message appears showing "Phonon: falling back to default playback engine" or something similar, but the audio worked fine. After update this message doesn't appears but the audio won't work at all (only amarok).

good point- i recall that i had done an update as well, and it's very likely that amarok was working fine before that time- i'll try the downgrade option and see what happens.

outlikeashoe, how did you perform the downgrade?

---

### Post by betweenthetines on 2009-04-05
> **Matt26 said:**
> outlikeashoe, how did you perform the downgrade?

Search for phonon in Synaptic. Select the package from the list, go to Package from the top menu and click Force Version (or just type Ctrl+E). Choose 4:4.2.0-0ubuntu (intrepid). 

Worked for me. Much thanks to outlikeashoe for the solution. :guitar:

---

### Post by betweenthetines on 2009-04-06
> **betweenthetines said:**
> Worked for me. Much thanks to outlikeashoe for the solution. :guitar:

It seems I spoke too soon. I was able to play one album but nothing else...still not sure why that one played.

Anyway, to enable a broader solution to my lack of audio in Amarok issue, I googled a little and found the following solution to the same problem:

"I removed the phonon-backend-gstreamer package [to ensure use of] the phonon-backend-xine package."

Upon doing the same, I can confirm that Amarok now plays full sound for all supported file types.

So, to repeat, use Synaptic or apt-get or whatever your usual method to remove the phonon-backend-gstreamer package, restart Amarok, and - voila - sound!

---

