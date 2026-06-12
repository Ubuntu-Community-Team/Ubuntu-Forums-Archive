---
title: "Bluetooth Headphones Problem a2dp"
date: 2008-07-12
forum: Networking &amp; Wireless
---

### Post by Cain67 on 2008-07-12
ok, i know there is alot out there on setting up bluetooth headsets.
however, i am still unable to get it working after 2 weeks.

i followed the instructions from :
[http://toolweb.wordpress.com/2008/05/13/setting-up-your-a2dp-enabled-bluetooth-headset-to-work-with-linux/](http://toolweb.wordpress.com/2008/05/13/setting-up-your-a2dp-enabled-bluetooth-headset-to-work-with-linux/)
[http://fosswire.com/2008/01/11/a2dp-stereo-linux/](http://fosswire.com/2008/01/11/a2dp-stereo-linux/)

i have also followed other threads instructions.

im using an Icombi bluetooth headset. 
most instructions seem to work until it becomes time to test.
in the terminal i get

>   $ arecord -D bluetooth -f s16_LE test.wav
ALSA lib pcm_bluetooth.c:1553:(bluetooth_init) BT_GETCAPABILITIES failed : Input/output error(5)
arecord: main:546: audio open error: Input/output error


under bluetooth settings in preferences, under services in audio devices it does show up, and using the .a2dp/toggle.sh i can direct sound from speakers to headset

however, i still get no sound.

i have also tried installing blueman, which allowed me to pair without any troubles, but again, no sound.

basically, i need to know where to go from here...
i can connect to the headset, i can see that the headset is connected, so how do i get the sound???

please help

---

### Post by Cain67 on 2008-07-12
ok, i now look like an idiot.

after pairing Blueman again, i went to sound settings, and saw under default mixer tracks, "BT Headset"

so music and movie sound (after hitting the test button) came though the headset.

using the movie player i get audio through headset :) (yay)
however sound events, and audio conferencing still come through main speakers.
am using a macbook if that has any effect.

but yea
i use vlc alot, and am now wondering if there is any easy way to set output through bluetooth for that?

---

