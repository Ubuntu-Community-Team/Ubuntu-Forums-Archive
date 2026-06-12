---
title: "cannot recorde sound on a youtube video"
date: 2010-07-01
forum: New to Ubuntu
---

### Post by noworldorder on 2010-07-01
Ubuntu 10.04

I tried recording a youtube video from my computer.  The video works five but there is no sound.

Any ideas??

---

### Post by Kimm on 2010-07-01
Not sure what you mean here, was there no sound at all, or only after you uploaded it to youtube?

If there is no sound at all your microphone is probably muted, so I suggest going to Sound Preferences and having a look in the Input tab (where you can select input device, and configure input volume).

If there is no sound only after uploading to youtube, it's a codec issue, so you'll have to either record in a different format, or convert the file in an application such as avidemux.

---

### Post by noworldorder on 2010-07-01
Hi

to clarify there is no sound prior to uploading.  I have the same issue with a sound recording program.  I checked in sound preferences and the mic is not muted.  Thanks - chris

---

### Post by Kimm on 2010-07-02
Then hopefully its just muted in alsa, open a terminal and type:

```

alsamixer

```

Then press F4 to modify settings for capture devices and check if any of the channels are muted (indicated by "MM" at the bottom), unmute by pressing the m-key while that device is selected.

If this doesn't help, it might be a driver issue and thats slightly beyond me, so I'd suggest asking in a different forum

---

