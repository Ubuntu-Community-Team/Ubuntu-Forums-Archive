---
title: "Audio help- Cant record audio or set up my internal mic"
date: 2009-10-17
forum: New to Ubuntu
---

### Post by zachary83 on 2009-10-17
Audio Help 

I Need help with getting my sound card to work inside Linux. At the moment I can hear sound online, from my audio files and such like, but cant record the sound through my laptop Mic. Also I cant seem to see the sound card drivers in the Hardware Drivers app, so cant activate. 

Any Ideas or answers would be a great help as Im a songwriter and constantly need to record demos onto my PC. 

I have a dell inspiron. 

Thanks in advance

---

### Post by mikewhatever on 2009-10-17
If you can here the sound, I'd assume the driver is installed and in use, besides, the Hardware Drivers utility is for restricted drivers only, drivers that aren't free to redistribute.
To get the mic working, open System->Preferences->Sound and try selecting a different capture interface. It usually says autodetect by default, but you can try Alsa or Pulseaudio.

---

### Post by zachary83 on 2009-10-17
Hi, thanks for the help so far. 

I have tried what you have suggested but unfortunately to no avail, I have also carried out a test on each option in the sound capture section, however I either got a no sound or just cackle.

Any more help would be greatly appreciated.

---

### Post by mikewhatever on 2009-10-17
Logically, testing the sound capture should work by using the mic and hearing the output from the speakers, but it doesn't. Every other button in the Sounds windows produces a beep, the one next to capture does not, nor does it reproduce the mic usage. I usually test the mic with Sound Recorder, a simply application under Applications->Sound&Video, or Skype test call.

---

### Post by zachary83 on 2009-10-17
Hi thanks I have try that as well but still no luck. Dont know what to do really, I also have problems with viewing video, dont think my drivers are working.

---

### Post by mikewhatever on 2009-10-17
One other thing to check is the capture volume level. Open Volume Control from the speaker icon on the top panel and make sure the capture slider isn't all the way down. While there, check the internal/external mic setting too.

---

