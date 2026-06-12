---
title: "headphones"
date: 2009-05-21
forum: New to Ubuntu
---

### Post by rlj399 on 2009-05-21
Sound keeps coming out from my laptops speakers even when i plug in my headphones. Sound is still transmitted to the headphones atleast, any fixes for this?

---

### Post by Aaardwark on 2009-05-21
To know if there are any fixes, I need more info on the sound card.

Could you give me the output from pasting the following in the terminal:
```
lspci | grep audio
lsmod | grep snd
```

---

### Post by Bölvaður on 2009-05-21
If this is an usb head phone then look on this forum for "pulse audio device chooser"

---

### Post by rlj399 on 2009-05-21
ok here's what i get
snd_hda_intel         557364  5 
snd_pcm_oss            52352  0 
snd_mixer_oss          24960  1 snd_pcm_oss
snd_pcm                99336  3 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          11524  0 
snd_seq_oss            41984  0 
snd_seq_midi           15744  0 
snd_rawmidi            33920  1 snd_seq_midi
snd_seq_midi_event     16512  2 snd_seq_oss,snd_seq_midi
snd_seq                66272  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              34064  2 snd_pcm,snd_seq
snd_seq_device         16276  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    78792  18 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              16800  1 snd
snd_page_alloc         18704  2 snd_hda_intel,snd_pcm

it's not a usb headset, just a regular ole' one

---

### Post by Settingsun00 on 2009-05-22
a

---

### Post by rlj399 on 2009-05-22
bump

---

### Post by koleoptero on 2009-05-22
This sounds weird. I thought the switch that stops the speakers is not dependant on software, but just a switch in the plug...

---

### Post by rlj399 on 2009-05-22
what do you mean a switch in the plug?

---

### Post by unutbu on 2009-05-22
rlj399, have you tried this:

Right-click on the gnome-panel. "Add to Panel" the Volume Control applet.
A little speaker icon should appear on the gnome-panel.
Right-click the speaker icon and select "Open Volume Control".
A window will pop up. Click the "Preferences" button.
You should see a number of "tracks" called things like Master, PCM, etc.
Select them all. Click close.
Now the window should show a volume control and mute icon for each track.
Play with them until you find the one that mutes the laptop speakers without disabling
the headphones.

---

### Post by asmoore82 on 2009-05-22
> **koleoptero said:**
> This sounds weird. I thought the switch that stops the speakers is not dependant on software, but just a switch in the plug...
sound chipsets went all freaky on us lately ...

Most modern PC's actually have 2 separate sound channels for the Microphone
depending on whether it's plugged in the back of the computer or on the front panel.
And they have those "7.1" channel systems where you have to plug your rear speakers
into the line-in port on the back of the PC ... all allegedly "auto-sensing" of course.

Just one more thing that the sound driver has to deal with that it shouldn't :rolleyes:

---

