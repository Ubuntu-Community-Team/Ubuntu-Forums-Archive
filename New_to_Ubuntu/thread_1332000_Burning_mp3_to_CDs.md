---
title: "Burning mp3 to CDs"
date: 2009-11-19
forum: New to Ubuntu
---

### Post by ColdLunch on 2009-11-19
I would like to burn an mp3 file to a CD and be able to listen to it in my car cd player.

What program should I use to do this?  Thanks.

---

### Post by Cheesemill on 2009-11-19
You can use Brasero, you'll find it under Applications > Sound & Video

Just select 'Audio project' and drag and drop your mp3's

---

### Post by dwasifar on 2009-11-19
I usually use K3B for that, because it integrates with Amarok and lets you burn your Amarok playlists right to CDs.

To install K3B, in a terminal window type this:```
sudo apt-get install k3b libk3b6-extracodecs
```

---

### Post by twisted_steel on 2009-11-19
If you do want MP3s on the CD rather than a standard audio CD with tracks, make sure to choose "Data project" rather than "Audio project".  Otherwise it will helpfully convert your MP3s to CD audio data.

---

### Post by Locke_99GS on 2009-11-19
Brasero integrates with GNOME; if you want to make a data CD, you can simply open the blank CD in nautilus and drag some files into it, then select "Write to disc." an it will burn the data CD.

---

### Post by dwasifar on 2009-11-23
> **twisted_steel said:**
> If you do want MP3s on the CD rather than a standard audio CD with tracks, make sure to choose "Data project" rather than "Audio project".  Otherwise it will helpfully convert your MP3s to CD audio data.

I think Audio Project is what he wants.  He said it's to play in the car.  I know some cars can play mp3 data discs, but I don't think it's all that common.

---

### Post by laidback on 2009-11-23
I'm so pleased I read these threads. I landed on Amarok and K3b way back in Ubuntu 6 and have been using them ever since, but I had never pressed the Burn to CD button in Amarok; integration, now that's a nice touch. Thanks for the tip dwasifar.

---

### Post by oldos2er on 2009-11-23
I have an older (1991) 5 disc CD player. In order to create audio CDs it would recognize, I use DAO mode, and burn at 1x (yes, 1x).

---

