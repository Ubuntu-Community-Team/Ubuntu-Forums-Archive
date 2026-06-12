---
title: "Recording with 'Audacity' or 'Ardour GTK2' under 'PulseAudio'"
date: 2010-06-18
forum: New to Ubuntu
---

### Post by Mega_Fauna on 2010-06-18
Is there an *audio recording program* which works under **PulseAudio** or do I have to go back to **ALSA**?

Does ***Ardour GTK2*** work? If so, how?


Has anyone got ***Audacity*** working under **PulseAudio**? Google isn't telling me much apart from killing **Pulse** and going back to **ALSA** which I'll only do in an emergency.

---

### Post by Mega_Fauna on 2010-06-23
Bump!

---

### Post by Mega_Fauna on 2010-06-30
Bump!

I fear ALSA is calling me?

---

### Post by Mega_Fauna on 2010-07-14
Audacity would only record a fraction of a second and has for the better part of a year on my system. Here, after about a day of hacking the problem, is my solution. Doubtless there is some overkill but I hope that this **HowTo** does help someone.

I first removed PulseAudio which may or may not have been a good idea. Certainly it was reinstated later on but right now we're all on ALSA.

[COLOR="Red"]**[SIZE="2"]AUDACITY SETTINGS[/SIZE]**[/COLOR]

From the [[COLOR="RoyalBlue"]_Ardour Manual_[/COLOR]]("http://en.flossmanuals.net/Ardour/WhatIsDigitalAudio") I learnt about Frequencies and samplings.

Setting *Audacity 1.3.9* to match:

Edit --> Settings --> Quality -->
[INDENT][INDENT]Default Sample Rate:	44100 Hz[/INDENT][/INDENT]
[INDENT][INDENT]Default Sample Format:	16-bit[/INDENT][/INDENT]

*Software Playthrough: Play new track while recording or monitoring (uncheck when recording "stereo mix")* == Unchecked



[COLOR="Red"]**[SIZE="2"]REINSTALLING PULSE TO WORK WITH ALSA[/SIZE]**[/COLOR]

Now it recorded, but could not recognize any input sound sources (i.e. Mix:0, Stereo Mixes, anything passing through the sound card such as a radio program).

I solved the endless silence with [[COLOR="RoyalBlue"]_this_[/COLOR]]("http://theaikenfamily.org/joomla/index.php?option=com_content&task=view&id=68&Itemid=31").

Then just for the record, Audacity 1.3.9 settings again:

Edit --> Settings --> Devices
[INDENT][INDENT]Interface Host:		ALSA[/INDENT][/INDENT]
[INDENT][INDENT]Playback Device:	pulse[/INDENT][/INDENT]
[INDENT][INDENT]Recording Device:	pulse[/INDENT][/INDENT]
[INDENT][INDENT]Recording Channels:	2 (Stereo)[/INDENT][/INDENT]


[COLOR="Red"]**[SIZE="2"]FINAL NOTES[/SIZE]**[/COLOR]

I should also add that in the process I upgraded to 9.10 - Karmic from 9.04 - Jaunty and drank a bit of wine to aid the virtue of patience. Please plan accordingly.

---

