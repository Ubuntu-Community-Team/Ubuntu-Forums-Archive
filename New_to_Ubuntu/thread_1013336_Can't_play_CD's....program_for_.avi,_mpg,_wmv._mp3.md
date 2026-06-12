---
title: "Can't play CD's....program for .avi, mpg, wmv. mp3/4 etc..."
date: 2008-12-16
forum: New to Ubuntu
---

### Post by luke0927 on 2008-12-16
Well i had problems with 8.10 and have installed 8.04 and everything is going well...I have sound and downloaded flash and can play vids on youtube...i put in a cd and i come up under rythmbox and it shows the songs titles etc...but it will not play any idea's on what to do or some other program i should try?

Also whats a good program to play other forms of media? mp3's etc....I would like to pull all my windows media player play list over.

Thanks

---

### Post by taurus on 2008-12-16
You need the media codecs.

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by luke0927 on 2008-12-16
I ran the commands and got all the updates but still nothing...when trying to play....any other ideas?

when i click the audio cd icon that comes up on the desktop the files are displayed as .wav and they have lock on the top of them...this is a store bought CD not a burned CD.

---

### Post by billgoldberg on 2008-12-16
Are the songs in the wma format?

If they are you'll need to click on the link in my signature called "codecs in ubuntu" and follow instructions.

--

It that isn't the case, you can try another player.

I suggest you try "banshee" or "exaile".

---

### Post by carml on 2008-12-16
You can look also for Gstreamer codecs,which can be found also under Applications->Add/Remove->Audio & Video:p.

---

### Post by luke0927 on 2008-12-16
> **billgoldberg said:**
> Are the songs in the wma format?

If they are you'll need to click on the link in my signature called "codecs in ubuntu" and follow instructions.

--

It that isn't the case, you can try another player.

I suggest you try "banshee" or "exaile".

The link in your sig fixed it in simple terms for my learning can you tell me what that did?  why did i need codecs and what are they?

---

### Post by wolfen69 on 2008-12-16
[Learn what codecs are]("http://en.wikipedia.org/wiki/Codec")

---

