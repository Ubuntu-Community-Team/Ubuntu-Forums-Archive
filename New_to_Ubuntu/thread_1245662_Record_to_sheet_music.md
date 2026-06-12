---
title: "Record to sheet music"
date: 2009-08-20
forum: New to Ubuntu
---

### Post by bethebunny on 2009-08-20
I'm looking for a piece of software that will allow me to play an electric instrument (or in general, any music), and attempt to transcribe it into sheet music.

I've just begun messing around with LMMS, which, while having most of the features of a modern operating system (its own windowing system, file browser and text editor) appears to lack the ability to record or import music files.

In particular, I'm looking for a piece of software that would allow me to record playing the piano through a 3.5mm audio jack and transcribe to a sheet-music and/or an LMMS-type format. Additionally, software that transcribes to guitar tabs would be pretty awesome, although de-mixing might pose a problem.

Also, any suggestions for better music editors are appreciated, as although LMMS appears very powerful, it seems to concentrate on a lot of features I'm not interested in at the expense of obfuscating simple composing features.

---

### Post by CatKiller on 2009-08-20
> **bethebunny said:**
>  In particular, I'm looking for a piece of software that would allow me to record playing the piano through a 3.5mm audio jack and transcribe to a sheet-music

I haven't looked at this specifically (although I am aware that all the pieces are available) but you're much more likely to have success with this if you have an electric keyboard connected to a MIDI port on your computer. To do it from audio would require some kind of awesome audio analysis just to work out what notes you're playing; using MIDI means that it's already in a form that your computer can understand.

Transcribing it to guitar tab might also be possible, but it's less likely to give satisfactory results. A given pitch can correspond to many different positions on the guitar. A computer is unlikely to pick the most comfortable one to play.

EDIT: MuseScore (which I happened to have installed anyway) is able to take an existing MIDI file and transcribe it to sheet music. Even if it can't take input directly from a keyboard (I haven't tried it) there are many ways to record your performance as a MIDI file.

EDIT 2: SongWrite is able to take a MIDI file and transcribe it to guitar tab. It made a reasonable fist of it, but, as I suspected, not the most comfortable to play.

---

