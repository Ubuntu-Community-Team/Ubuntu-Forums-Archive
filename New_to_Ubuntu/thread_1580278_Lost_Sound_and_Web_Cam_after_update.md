---
title: "Lost Sound and Web Cam after update"
date: 2010-09-23
forum: New to Ubuntu
---

### Post by Ignorance Isnt Bliss on 2010-09-23
my system updated yesterday and since the update I am unable to get any sound from my eeepc 900a's speakers or headphones plugged into the head phone socket. The web cam has also stopped working. 

I downloaded the update without any intervention from me, and I can't think of anything else I've done to cause the problem.

The speaker symbol on the bar at the top of the screen shows no volume but when I left click on it it has the volume turned up full but the "mute all" button is greyed out. 

If I click on "Sound Preferences" the out put  volume is on full but the Input volume is greyed out and on zero.

The output device is Dummy output stereo. That doesn't seem correct to me but it is the only choice. 

I tried the system test in System- Administration and didn't get any sound from that either.

The web cam doesn't work in Ekiga even though it did two days ago. Obviously the sound doesn't work in Ekiga either.

There is always a chance I hae done something dumb but can't think what it could be.

Has anyone else had the same problem?

Help Please    :confused:

---

### Post by Ignorance Isnt Bliss on 2010-09-23
More info

I tried aplay -l in a terminal and was told

aply: device_list:223: no soundcards found

I hope this provides a clue to those who know abut Ubutu (I don't)

---

### Post by Ignorance Isnt Bliss on 2010-09-23
I seem to have fixed this problem by running

sudo apt-get purge pulseaudio && apt-get install pulseaudio
 
This seemed to remove audio settings but didn't seem to re install anything so I guessed 

sudo apt-get install pulseaudio

I then shut down (it didn't shut down properly just restarted, so held the on off button down until it did). I then restarted and have web cam and sound although I have no speaker Icon anymore.

I don't know if the system will now shut down properly yet but  [I]am a long way further forward.

I hope this may help others with similar problems, but before you try my fix bare in mind I know nothing about computers or software. I got to this fix by guess work and it might have just been the forced shut down that fixed it for all I know!
[/I]

---

### Post by lkjoel on 2010-09-24
> **Ignorance Isnt Bliss said:**
> my system updated yesterday and since the update I am unable to get any sound from my eeepc 900a's speakers or headphones plugged into the head phone socket. The web cam has also stopped working. 

I downloaded the update without any intervention from me, and I can't think of anything else I've done to cause the problem.

The speaker symbol on the bar at the top of the screen shows no volume but when I left click on it it has the volume turned up full but the "mute all" button is greyed out. 

If I click on "Sound Preferences" the out put  volume is on full but the Input volume is greyed out and on zero.

The output device is Dummy output stereo. That doesn't seem correct to me but it is the only choice. 

I tried the system test in System- Administration and didn't get any sound from that either.

The web cam doesn't work in Ekiga even though it did two days ago. Obviously the sound doesn't work in Ekiga either.

There is always a chance I hae done something dumb but can't think what it could be.

Has anyone else had the same problem?

Help Please    :confused:
Try Fix your sound! in my signature.
Then use Post-Fix your sound! in my signature.

---

