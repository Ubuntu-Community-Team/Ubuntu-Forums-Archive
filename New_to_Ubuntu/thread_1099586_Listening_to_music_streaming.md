---
title: "Listening to music streaming"
date: 2009-03-18
forum: New to Ubuntu
---

### Post by Fabzil on 2009-03-18
Hello !


Can you tell me how can I listen to the streaming on this website ?
[http://www.surfmusic.de/dslformat/reggae.html]("http://www.surfmusic.de/dslformat/reggae.html")
I can listen to the MediaPlayer ones with Totem firefox plugins, but the RealPlayer ones I can't

Thx for your help !;););)

---

### Post by rburkartjo on 2009-03-18
golook, i just tried also using ff i cant find any avial plugin that will work that happens sometimes

---

### Post by klemes on 2009-03-18
You must have mplayer  mozilla plugin:

```
sudo apt-get remove totem-mozilla
sudo apt-get install mplayer mozilla-mplayer
```

Then restart your browser and go test it in your preferred site.

---

### Post by Fabzil on 2009-03-18
> **klemes said:**
> You must have mplayer  mozilla plugin:

```
sudo apt-get remove totem-mozilla
sudo apt-get install mplayer mozilla-mplayer
```

Then restart your browser and go test it in your preferred site.

I will try this and if it works that will be cool ! ;)

But I hope the old ones that worked will still be working...:(


EDIT : I've done what you've said. I cal still play the old ones that used to work, but with a nice player menu. Thx ;) ! But, still on _[this website](http://www.surfmusic.de/dslformat/reggae.html)_, the "Listen live !" with the real player icons doesn't work    : /

---

### Post by Fabzil on 2009-03-19
Any ideas ?

I tried with** vlc** but It won't works (or maybe it will but I configured it too badly ?)

---

### Post by andrew.46 on 2009-03-19
Hi GoLookAndKill,

> **GoLookAndKill said:**
>  But, still on _[this website](http://www.surfmusic.de/dslformat/reggae.html)_, the "Listen live !" with the real player icons doesn't work    : /

Use the 'Standalone Player' link. Example:

```
mplayer -playlist http://www.reggae-vibes.fr:8000/listen.pls
```

Andrew

---

### Post by Fabzil on 2009-03-23
**Yeah ! This is it ! It works ! **

Woohoo ! :popcorn:


Thx ! NOT convenient :( , but sill working...;)

---

