---
title: "Bad sound with MIDI (Rosegarden) / JACK X runs up the wazoo"
date: 2008-12-15
forum: New to Ubuntu
---

### Post by BigRicky on 2008-12-15
I am pretty much a complete newbie, my Linux experience being somewhere around nil.  I have managed to get Rosegarden (Which is the main thing that attracted me to Linux) to cooperate with QSynth through JACK, but it sounds like someone blew a speaker, repaired it, then blew it again.  I experience the same thing with Virtual MIDI keyboard sent to ZynAddSubFX, but MIDI sounds fine when using Timidity++ to play MIDI songs.  

Also, I started up JACK, ate dinner, came back, and I had almost a thousand Xruns.  In an hour!  This is with Frames/Period set to 1024.  A guide I read said to put it at 64, but JACK will not even start at that low.  That same guide also said to hit the "realtime" button in JACK's settings, but JACK refuses to run with that option checked.  I am running the realtime kernel, or at least I think I am, as I installed it in Synaptic and it required a reboot.  

While my computer isn't top of the line, it sure isn't hurting, either.  I've got a dual core Athlon 64 5000 series something or other, 4 gigs of RAM, and I'm currently using my Gigabyte brand motherboard's sound card, which is an Intel.  I have a couple of Sound Blaster Live cards, so if anyone thinks that moving to one of those will help, I'll give it a whirl.  

I've done a few hours searching these forums and Googling and haven't come up with anything...  Any help is greatly appreciated.

---

### Post by BigRicky on 2008-12-16
UPDATE:
This is getting really freaking weird!  So I got quality sound out of Rosegarden by not running the JACK server.  _[Here](http://i106.photobucket.com/albums/m246/El_Ornitorrinco/Screenshot-Connections-JACKAudio-1.png)_ I am running the JACK sever, getting dozens of Xruns a minute (honestly, I think I'm getting a lot more than I did before I installed the realtime kernel.  It was bad, but not anywhere near this...) and getting horrible sound.  But _[Here](http://i106.photobucket.com/albums/m246/El_Ornitorrinco/Screenshot-Connections-JACKAudioCon.png)_ I am do NOT have the JACK server running.  I set the QSynth driver to ALSA, not JACK, and then connected Rosegarden to QSynth using JACK, but without running the JACK server.  Rosegarden complained at bootup, but I got sound!  Also, I can move the connection from QSynth to Timidity and use the soundfont I loaded into Timidity.  How does JACK send the sound from Rosegarden to QSynth or Timidity if the server is not running?  I still want to fix the Xruns...  I'd like to do this the way it's meant to be done, but I've got good sound!

---

