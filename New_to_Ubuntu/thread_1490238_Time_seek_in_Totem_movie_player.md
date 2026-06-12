---
title: "Time seek in Totem movie player"
date: 2010-05-22
forum: New to Ubuntu
---

### Post by Rushyang on 2010-05-22
Bonjour Guys,

When I press right arrow key in Totem movie player, while playing a movie, I skips 1 minute. & When I press Left Arrow key, I skips like 15 seconds. 

What If I want to change it to any seconds I prefer? 

If it's not possible, Is there any movie player out there, In which I can assign a Time Jump what I want?

---

### Post by mixmastamyk on 2010-05-22
Totem is a bit lame, but most media players have a control panel or preferences where you can configure the keys to do what you want.

It's likely you won't be able to change between 15 and 16 seconds, but maybe 5,10,60 etc.

---

### Post by fela on 2010-05-22
Mod mplayer to make a variable for time skipping measured in milliseconds. After all, it's open source ;)

...if you have the time...

---

### Post by Rushyang on 2010-05-23
> **fela said:**
> Mod mplayer to make a variable for time skipping measured in milliseconds. After all, it's open source ;)

...if you have the time...

Alright, I'm all ears. But, How to do that? :confused:

---

### Post by fela on 2010-05-23
> **Rushyang said:**
> Alright, I'm all ears. But, How to do that? :confused:

It was a bit of a joke (sorry!). You'd have to look through the source code and add that feature.

But I'm pretty sure mplayer already has that capability - so you should try that player.

```
sudo apt-get install gmplayer
```

(I think gmplayer is the GTK graphical version of it - if you just install mplayer you'll get a command line player - ie launched only from the command line.) Of course you can also install from add/remove.

---

