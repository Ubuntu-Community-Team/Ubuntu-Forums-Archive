---
title: "Sound card not recognised"
date: 2009-05-05
forum: New to Ubuntu
---

### Post by cessite on 2009-05-05
After doing an update in 8.10 my sound stopped working. I tried reinstalling ALSA but that made things worse so I just waited for 9.04, hoping that would fix things.

Although 9.04 seemed to eradicate the error messages, I still have no sound. I've read all the forum threads on sound not working and tried every bit of advice given. I've reinstalled ALSA but whatever I do, the sound card is not seen.

'lspci | grep -i audio' gives: 00:10.2 Multimedia audio controller: nVidia Corporation MCP51 AC97 Audio Controller (rev a2).

I have Windows XP on the computer too, and in there the sound card is called Realtex AC97. It works ok with XP.

'lshw -C sound' produces:
  *-multimedia UNCLAIMED  
       description: Multimedia audio controller
       product: MCP51 AC97 Audio Controller
       vendor: nVidia Corporation
       physical id: 10.2
       bus info: pci@0000:00:10.2
       version: a2
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0 maxlatency=5 mingnt=2

...which shows that the card is there but it is unclaimed by any driver.

When I go to System>Preferences>Sound on 'Default Mixer Tracks' it gives Null for both Playback and Capture.

If I select ALSA for any of the Test buttons I get:
'audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open audio device for playback.'

Can anyone tell me how to get the software to recognise my sound card?

Thanks

---

### Post by jerrrys on 2009-05-10
i had trouble with 810...the fix that worked for me was to switch to 804...

should also say that im not running your sound card, but still 804 just seems to work

---

