---
title: "youtube and skype not working fully"
date: 2009-10-14
forum: New to Ubuntu
---

### Post by hughcrowther on 2009-10-14
Cannot get skype internal mic to work and youtunbe to perform properly without stopping either video or audio any ideas (acer aspire 5315 running 9.04) used to work ok with 8.04 & 8.10 but how to downgrade?

---

### Post by dvlchd3 on 2009-10-15
I'm not sure about the mic.  Do you have audacity or some other recording software installed.  If so, you may try recording something through that mic.  This will tell us whether it is a skype issue, or mic issue.

As far as Youtube, are you sure you have all the appropiate plugins installed.  Can you post Firefox's plugin list (in Firefox's address bar, type 'about:plugins' (w/out quotes) and press Enter).  I believe you need to have gstreamer and some restricted extras installed for Youtube to function properly.

---

### Post by hughcrowther on 2009-10-15
Tried the internal mic and a plugin one also a usb plugin - nothing
tried it on 'sound recorder' and 'audacity' checked the pulse settings on volume control and also alsa mixer all set ok - I do get the sound playback from skype so one half is ok just nothing on all the input systems - skype is the latest release all others have been updated to the latest relase.
 Before I upgraded to 9.04 everything was working fine, even youtube, now just a mess.
As for plugins to ff,  Firefox/3.0.14, have lots of plugins but not gtreamer or other stuff will look into that.

---

### Post by kiridude on 2009-10-15
Check volume control > recordings and make sure you have "capture" and "digital" enabled. Also, my mic was muted by default, so un-mute on the recordings window.

---

### Post by hughcrowther on 2009-10-15
still nothing!

---

### Post by SirBismuth on 2009-10-15
I have a USB headset, and use PulseAudio to get the microphone working in skype.  To get the mic. working in skype, I had skype loaded, then went into pulseaudio's volume manager, and change the input channel from my soundcard to the usb mic., and now all is good.

youtube might be something to do with plugins, post your list as someone requested.

B

---

### Post by hughcrowther on 2009-10-15
tried but still no joy.

---

### Post by alan tait on 2009-10-21
For me it's always a tremendous pain in the **** getting sound out of Skype on Ubuntu, which is a great pity, cos everything else is great. A developer told me that it was a conflict between Firefox and Skype fighting over the audio, but I can't follow that up. Any use to you?

---

### Post by lavinog on 2009-10-21
> **hughcrowther said:**
> Cannot get skype internal mic to work and youtunbe to perform properly without stopping either video or audio any ideas (acer aspire 5315 running 9.04) used to work ok with 8.04 & 8.10 but how to downgrade?

I wouldn't try and downgrade with 9.10 being released in a couple of days.  9.10 might fix it.

You have two different issues.  I would suggest making two separate threads.

Your skype problem doesn't look like a problem with skype, but a problem with your microphone or mixer.  Post some screenshots of your mixer.

Your flash video problem can be a large number of things.  Can you be more specific as to what youtube is doing?  Is the video blank, or is the framerate too low...etc?

Also are you using ubuntu 64bit?  If so the default flash plugin has some issues because it is 32bit.

---

### Post by hughcrowther on 2009-10-21
Ok will wait for 9.10
I agree probably not Skype problem, the entire input system via mic, line in, USB or stereo input jack will not reconise any form of input.
I have tried all the volume control bits from pulse and alsa - all levels are up and no mutes have checked alsa version and pulse on terminal and all possible relevent instalations on  synaptic package manager.

As for you tube got it working perfectly on empathy web browser, so fixed.

---

### Post by alan tait on 2009-10-22
Hugh,
Update re. my last post: have tried the Skype beta from their website, and now seems to work fine on both my laptops. On one I had to uncheck the box in Options> Sound Devices > "Allow Skype to automatically adjust my mixer levels". But not on my other laptop. Weird.

---

### Post by hughcrowther on 2009-11-03
Nope still dead as before!!! any ideas anyone?

---

