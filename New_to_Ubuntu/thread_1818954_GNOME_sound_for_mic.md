---
title: "GNOME sound for mic?"
date: 2011-08-05
forum: New to Ubuntu
---

### Post by Foobarz on 2011-08-05
Ok, I think mic in the GNOME sound preferences is really weird. My sound card is set to Internal Audio (Analog Sterero Duplex). The digital options (eg Digital Duplex) do not work. I also have a built-in webcam and mic. My question is, how come whenever I plug a mic into the mic jack, I have to go to sound preferences and change the audio connector to analog audio. Whenever I need to use the internal mic, I have to go there again and change the audio connector to internal audio. Is there some way to make it so I don't have to do this everytime I plug a mic into the mic jack?

---

### Post by Foobarz on 2011-08-11
Poke!

---

### Post by amjjawad on 2011-08-11
What is your Ubuntu Release?

---

### Post by CatKiller on 2011-08-11
> **Foobarz said:**
> My question is, how come whenever I plug a mic into the mic jack, I have to go to sound preferences and change the audio connector to analog audio. Whenever I need to use the internal mic, I have to go there again and change the audio connector to internal audio

Because the tool is very simple and is only set up for one input and one output.

> Is there some way to make it so I don't have to do this everytime I plug a mic into the mic jack?

Probably. It's also probably very complicated. [This]("http://www.linuxquestions.org/questions/linux-software-2/alsa-and-pulseaudio-recording-multiple-input-devices-877614/#post4341696") describes someone doing similar - combining two inputs into one so that he could record both of them together - but you're probably better off just manually switching, tbh.

---

