---
title: "Sound Themes"
date: 2009-06-02
forum: New to Ubuntu
---

### Post by CaptainMark on 2009-06-02
I know this probaly sound royally stupid, but is there a way to change your sound theme on 9.04. If I go to System>Preferences>Sounds and select the sounds tab theres no option to add a theme and i have to change them all seperatley and it takes ages,
Ive got a bunch of sound packs from Gnome looks and there must be an easy way to install them all.
Any help?

---

### Post by 243kof on 2009-06-03
Hi, you need to copy your sound theme folder to /usr/share/sounds. Don't forget that you don't own this folder, so you have to use sudo. For example, type "gksudo nautilus" in the terminal, navigate to the path I mentioned earlier and paste your sound theme there! Then it will (hopefully) appear as an option under System->Preferences-> Sound-> Sounds tab-> Sound theme. Good luck :)

---

### Post by CaptainMark on 2009-06-03
Ive tried this, Ive extrcated the files and plonked them in a folder in sounds, no good. Does it need an index, the ubuntu theme folder has got an index but the sound folders I unpacked dont, does this make any difference??

---

### Post by Therion on 2009-06-03
There's a bit of trick to doing this but yes, it can be done.  I used to have a little guide around somewhere with instructions.  You do have to use sudo nautilus to copy the files over, they need to be .wav files as I recall (though I also seem to recall .mp3 was acceptable) and then you have to adjust your settings to use the new sound files in the Sounds/Preferences menu.  

There are some good sound themes on Gnome-Look and I think the one I used was called Dream...  I'll see if I can't find that guide I used to use for this... It was very helpful.

---

### Post by CaptainMark on 2009-06-03
Seems a lot of effort for something i assumed would be simple. At the moment i have to find each sound i want and change i manually, its not a big deal, just tedious and it would be nice to just flip and change between sound themes whenever i feel like a change.

---

### Post by Therion on 2009-06-03
> **CaptainMark said:**
> Seems a lot of effort for something i assumed would be simple. At the moment i have to find each sound i want and change i manually, its not a big deal, just tedious and it would be nice to just flip and change between sound themes whenever i feel like a change.
Agreed.  Changing sound-themes is not as easy as changing, say, your GTK theme where you just pick a new theme, click "Apply" and... *Voila!* 

Sound themes ARE a tad tedious, unfortunately.

<shrug>

---

### Post by CaptainMark on 2009-06-03
This should be worked on, perhaps someone will make a tool for loading themes up in groups quickly and easily, would be nice.  You contributors out there have a new mission.

---

