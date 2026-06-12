---
title: "No Sound when Playing midi files"
date: 2009-03-11
forum: New to Ubuntu
---

### Post by John Hale on 2009-03-11
When using Kmid I get no sound when playing files is there like a media player equivalent for ubuntu that'll do it all?

---

### Post by martrn on 2009-03-11
From the terminal :

```
sudo apt-get install timidity
timidity -ig
```

Check you can play a midi file.

[http://www.rosegardenmusic.com/]("http://www.rosegardenmusic.com/") plays and edits midi files.

kmidi takes some jigger poker to get midi's to play, and requires the proper sound card / alsa kernel models to be set up correctly for kde to play midi's properly through you midi sound card.

---

