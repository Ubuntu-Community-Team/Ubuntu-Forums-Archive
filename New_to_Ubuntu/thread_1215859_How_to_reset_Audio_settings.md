---
title: "How to reset Audio settings?"
date: 2009-07-17
forum: New to Ubuntu
---

### Post by ben105 on 2009-07-17
[SIZE=2]Hi to all

Switching from Windows, I have been using Ubuntu for one week and I am quite happy.

There is only one problem: While testing how to record live online radio, I changed my audio settings.

Now, if I listen through the headset to music, my music seems to play more quiet then before if I turn on the volume (nearly the end of the volume scale) then I have a very strong noise. 
It was my fault that I didn't take screenshots of these before, but I didn't expect problems. 

That are my details:

Ubuntu 9.04
Acer Aspire 5735Z
Headset by Plantronic

I can choose in[/SIZE][SIZE=2] Audio Device: [/SIZE]
[SIZE=2]HDA Intel (Also Mixer)
Realtec ALC 268 (OSS Mixer)
Playback HDA Intel-ALC268 Analog (which I'm using at the moment, however all other also didn't reduce the noise)
Capture: Monitor of HDA Intel ALS268 (Pulse Audio Mixer)
Capture: HDA Intel ALS268 (Pulse Audio Mixer) 

Is there something in the Volume Control what I can change?

And if you could write to me which program and settings I have to choose in order to record live radio, that would be great.

T[/SIZE][SIZE=2]hank you in advance[/SIZE]

---

### Post by nwadams on 2009-07-17
so I don't know much about recording live radio, but a little about recording audio. 

try this. where the sound icon is on the tray bar. right click on it and go properties. and there should be a little window that opens that lists the 5 audio devices (as you have below). the HDA intel (alsa mixer) one will probably be selected. Change it to the Playback HDA Intel-ALC268 Analog one. and now try the volume.

Post back if that works or does not work and we will continue to try things if neccessary.

nwadams

---

### Post by ben105 on 2009-07-17
Thank you very much.

I have tried but -unfortunately- it didn't work.

I tested all settings and noticed a movement in the level, but there was no sound recorded only very loud noise.

Also that I have this noise while listening to music makes me mad. 

I very hope I haven't changed my settings completely.

---

### Post by ajgreeny on 2009-07-17
Assuming this is streamed radio you are recording, you can do it with a direct stream dump to hard disk using mplayer in the command line, very useful if you have a specific program to record.  I have several bash script files using those commands, which I can run with cron to time recordings as well.
```
mplayer -cache 2048 <URL> -dumpstream -dumpfile stream.mp3
```is for mp3 streams to save as mp3, and 
```
mplayer -cache 2048 <URL> -vc null -vo null -ao pcm:fast:waveheader:file=filename.wav
```for other streams, eg real, to save as wav, which you can then convert to mp3, or other file type..  Look out for some streams that are actually in playlist form and if the real stream gives you errors, try adding -playist to the front of the URL.

---

### Post by ben105 on 2009-07-18
[SIZE=2]To be honest that system seems to be a bit doggy. To check the noise problem, I opened the movie player this time and noticed that moving the sound level doesn't have influence on the "volume control". I clicked [/SIZE][SIZE=2]on the mute/unmute buttons[/SIZE][SIZE=2] in the volume control and suddenly the sound disappeared completely. There is also a problem with "PCM". If I click "mute" and "unmute" again, then there is no sound and I have to change the levels by hand. If I "mute" it, then I get a clicking sound.

I don't know if it's a problem of Ubuntu. I only know that on my Windows system, I heard the same song with Level 1 and getting the same level here, I have to move it to 50%. (It's 6 o'clock in the morning and quiet outside. If I turn it more louder, then the noise by the headphones also rises.) 

Could you tell what the standard settings in System - Preferences - Sound are? Or is there any chance to get the entry level down from 50 % to 10%?

Regarding the direct stream, sometimes I record [/SIZE][SIZE=2]interesting dramatisations[/SIZE][SIZE=2] from BBC iPlayer so that I can listen to them when I have time and not when I have to do it. BBC iPlayer doesn't have a direct link; it's more like a page with flash player.
Nevertheless, I keep it on and will test it.
[/SIZE]

---

