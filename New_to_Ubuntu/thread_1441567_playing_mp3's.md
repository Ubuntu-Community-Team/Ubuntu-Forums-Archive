---
title: "playing mp3's"
date: 2010-03-28
forum: New to Ubuntu
---

### Post by rcah on 2010-03-28
I tried to player an mp3 and was not able to download codec. can not find vlcplayer. checked update manager and it wants to download 247 updates, and I thought microsoft sucked. Any Help?

---

### Post by derekeverett on 2010-03-28
Run these two commands in your terminal
```

sudo apt-get install ubuntu-restricted-extras

```

and

```

sudo apt-get install vlc

```

It was your charming attitude that convinced me to reply ;)

---

### Post by n0dix on 2010-03-28
But why to use vlc player to play a mp3 file, instead use Rhythmbox or Totem.
Probably you need gstreamer (bad - ugly - good)

---

### Post by derekeverett on 2010-03-28
> **n0dix said:**
> But why to use vlc player to play a mp3 file, instead use Rhythmbox or Totem.
Probably you need gstreamer (bad - ugly - good)

You don't need VLC player to play an mp3. But he asked how to get VLC....

Probably for videos and such.

---

### Post by nemilar on 2010-03-28
I like how derekeverett's signature so perfectly matches the OP of this thread.

---

### Post by lyall on 2010-03-28
Hi and Welcome to Ubuntu forums

RestrictedFormats [https://help.ubuntu.com/community/RestrictedFormats]("https://help.ubuntu.com/community/RestrictedFormats")

Community Documentation good place to answer alot of your questions about Ubuntu
- TitleIndex
[https://help.ubuntu.com/community/TitleIndex]("https://help.ubuntu.com/community/TitleIndex")
also read the forums -Absolute Beginner Talk and look at the first thread
Free Beginners Guide and  New to Ubuntu? Start here...

good luck and have fun learning

---

### Post by derekeverett on 2010-03-28
> **nemilar said:**
> I like how derekeverett's signature so perfectly matches the OP of this thread.

Thanks :D

That signature is from me "learning from my own mistakes" when it comes to dealing with computers..

---

### Post by tom.swartz07 on 2010-03-28
> **rcah said:**
> I tried to player an mp3 and was not able to download codec. can not find vlcplayer. checked update manager and it wants to download 247 updates, and I thought microsoft sucked. Any Help?

To be honest, it seems that youre still sitting on a ton of updates from when you first installed. 

Not to be 'That Guy', but you really should install them sometime soon- they clear up some really serious security holes and problems that could possibly crash your whole box. Best part is, you generally dont have to restart (unless you install a new kernel image)

Once you get them installed, youll be lucky if there are 5 a month! :D

---

