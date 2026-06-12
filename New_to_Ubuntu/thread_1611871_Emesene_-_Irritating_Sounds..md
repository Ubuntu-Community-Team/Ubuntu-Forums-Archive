---
title: "Emesene - Irritating Sounds."
date: 2010-11-02
forum: New to Ubuntu
---

### Post by guy531 on 2010-11-02
Hello. I'm new with Ubuntu so please be patient with my lack of understanding :-)

I have recently installed **Emesene** - A program wich you can use as a replacement for windows messenger, After I tried kmess and it didn't work well...

The program it self is very easy to use and simple. My only problem with it is the sound.

The default sound of the program is **very irritating**, And since the program itself has no option of just doing a pop up or something when someone logs in, I am dependent on this sound to know when someone is sending me messages or logging in.

In contrast the **Skype** sounds are very pleasant to the ear...

My question is, Is it possible to import the sounds of Skype, in to Emesese, and use them instead? Or at least switch it to any other sounds?

Thank you very much, And I hope to have many pleasant years of Linux :D.

---

### Post by NESFreak on 2010-11-04
hi,

emesene has in fact the ability to use sound themes.

These are selectable under options-->preferences-->sounds

you could easily create your own. The themes are stored under
```
/usr/share/emesene/sound_themes
```
just create a new directory. Copy your skype sounds there and rename them according to the names that emesene expects.
```
alert.wav  nudge.wav  offline.wav  online.wav  send.wav  type.wav

```

---

