---
title: "cannot record sound"
date: 2009-01-26
forum: New to Ubuntu
---

### Post by srtpg2 on 2009-01-26
hi 

i have installed ubuntu a few days back and i cannot for the life of me record sound in ubuntu. i have tried a million things in ALSA mixer and what not. i have HDA intel Realtek ALC268 and I have an HP pavilion DV6835nr. thanks so much in advance.

srtpg2

---

### Post by candtalan on 2009-01-26
My sympathies, however do not panic! I have sometimes found this in various machines. I am not sure there is any one easy quick answer for all circumstances.

I now use audacity to record stuff, although it often needs a lot of setting up with Mixer choices. I have not often had success with the ubuntu (default install) sound recorder. Maybe I am not familiar enough with that one.

I have often installed the gnome alsa mixer (gnome-alsamixer) which showed lots of stuff to choose.

Audacity has options to be set if required: Edit>preferences, then consider the Playback and the Recording Devices. Changes to these need to be made with no sound file loaded into audacity.

If no success at first, be patient and try things in as systematic a away as you can. Master, PCM, Capture: (check 'Rec' yes), are all usually important, but you might need  more.

As an unusual exception, one machine simply did not work at all like this (a new machine of a friend, I think too new and sound drivers were not complete in the available distro at that time), and I ended up using a Y cable from the speaker out with one leg going to the speakers and th espare leg going to the 'Line In'.

hth

---

