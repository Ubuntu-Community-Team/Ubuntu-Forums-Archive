---
title: "Sound Recording from the system sound"
date: 2009-08-11
forum: New to Ubuntu
---

### Post by akkad on 2009-08-11
am looking to record a music from a website that is played via adobe flash, i have pointed to main menu>>sound & video>>sound recorder, in the "record from input" i have one option only that is "capture", i selected it and recorded but with no sound at all, the recorded file is silent, what should i do??

---

### Post by bdentremont on 2009-08-12
I am not sure the answer to your question on recording, but I do know that I have downloaded FLV videos (for example YouTube) and opened them up in Avidemux to extract the sound channel and save it to MP3.

---

### Post by akkad on 2009-08-12
> **bdentremont said:**
> I am not sure the answer to your question on recording, but I do know that I have downloaded FLV videos (for example YouTube) and opened them up in Avidemux to extract the sound channel and save it to MP3.

no this is not the case, consider any thing is playing music in ubuntu, like playing music over some audio player, a movie, or viewing a video in youtube, this means that the system sound is playing something, am looking to record what else the system sound is playing, to do so i'll need a software to record the system sound, so i think this is the functionality of the sound recorder that come by default with ubuntu, but as i told the record is silent, i think it is a matter of some configuration.

---

### Post by tominsf on 2009-09-07
Some sound card/sound chip implementations (on motherboards, for instance) seem to make it impossible to record the pwm stream, even though the chip itself may be capable of it.  I use this workaround:  I plug the output from the headphone (or line) jack into the input (mic) jack.  You should then be able to fiddle with the capture sliders and switches (under the recording tab) and the mic or line-in slider in the playback tab to get it to record.

---

