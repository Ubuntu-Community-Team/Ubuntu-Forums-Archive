---
title: "Internet Radio Stream Unstable"
date: 2011-01-30
forum: New to Ubuntu
---

### Post by BNZBKK on 2011-01-30
Internet Radio Stream Unstable

 ...if and when it chooses to connect, where do I start ?

---

### Post by andrew.46 on 2011-01-30
Can you give the address of the stream?

---

### Post by BNZBKK on 2011-01-30
Yes, 

[http://www.jazzandblues.org/programming/listen/stream/](http://www.jazzandblues.org/programming/listen/stream/)


Thankyou

---

### Post by BNZBKK on 2011-01-31
Anybody ?

---

### Post by ron999 on 2011-02-01
> **BNZBKK said:**
> Anybody ?
This is a stream that will play with mPlayer or VLC:-
```
http://1.ice1.sa.streamaudio.com/kkjz_fm.mp3
```

---

### Post by BNZBKK on 2011-02-01
Thank you ron999 but my problem started when KKJZ recently switched over to *'streamaudio.com*' and *'http://1.ice1.sa.streamaudio.com/kkjz_fm.mp3'*  inserted in VLC and Movie Player does nothing, however I could be doing it wrong

---

### Post by ron999 on 2011-02-01
It's playing OK for me.
Try it from command line first:-
```
vlc http://1.ice1.sa.streamaudio.com/kkjz_fm.mp3
```

---

### Post by marl30 on 2011-02-01
> **BNZBKK said:**
> Yes, 

[http://www.jazzandblues.org/programming/listen/stream/](http://www.jazzandblues.org/programming/listen/stream/)


Thankyou

You shouldn't be having problem playing this stream if you have the latest flash player installed. I'm playing it right now and it appears to be using flash, at least that's what it says is required at the bottom. 

I may keep this link as well. I like how nice and soothing these jazz music are. :)

---

### Post by weedeater64 on 2011-02-01
I can not connect, several tries.

apt-get install streamtuner

---

### Post by marl30 on 2011-02-01
> **weedeater64 said:**
> I can not connect, several tries.

apt-get install streamtuner

I would want to think those having trouble playing this stream may not have the ubuntu-restricted-extras plugins intalled.

---

### Post by BNZBKK on 2011-02-03
I installed 'Streamtuner' and it was terrific ..until I tried to insert the kkjz.org station. Now after 'Removing' and 'Installing' several times I get nothing.

1. How do I 'Reset Defaults' in Streamtuner ?

2. Or the default line for Xiph ?

---

### Post by marl30 on 2011-02-03
> **BNZBKK said:**
> I installed 'Streamtuner' and it was terrific ..until I tried to insert the kkjz.org station. Now after 'Removing' and 'Installing' several times I get nothing.

1. How do I 'Reset Defaults' in Streamtuner ?

2. Or the default line for Xiph ?
I formated and reinstalled today. Saw this thread once again and decided to test the link. Still working for me. All I did so far was to install the restricted extras, then use the flash-aid firefox plugin to install the latest 64 bit flash. I do hope you get it sorted out.

---

