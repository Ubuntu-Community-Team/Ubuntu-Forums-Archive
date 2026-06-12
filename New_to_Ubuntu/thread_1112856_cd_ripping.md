---
title: "cd ripping"
date: 2009-04-01
forum: New to Ubuntu
---

### Post by ave2 on 2009-04-01
there are so many options when it comes to cd ripping to mp3 software as well as dvd ripping, what would you recommend for each of those- all I wont is something simple, and fast

---

### Post by nothingspecial on 2009-04-01
I like [COLOR="Red"][grip]("http://nostatic.org/grip/")[/COLOR].


It`s usefull if you have a large amount of cds to do because you can set it to start ripping on insert and automatically eject when finished. So you can get on with something else and just pop another cd in when the tray opens.

---

### Post by ave2 on 2009-04-01
Iv just tried grip- everything looks great, but I cant figure out how to configure the "save to" directory

---

### Post by nothingspecial on 2009-04-01
In the tabs Config > Encode > Options where it says M3U file format ~/ogg/%A-%d.m3u.

This is saying put the track in an Artist folder in a folder called ogg in your home directory change it to whatever you want eg ```
~/Music/ogg%A-%d.m3u
``` or if you want your music on an external drive called disk
```
/media/disk/%A-%d.m3u
```.

Or in a folder called bananas in your Pictures folder ```
~/Pictures/bananas/%A-%d.m3u
```

You get the idea.

---

### Post by ave2 on 2009-04-01
makes sense- thanks

---

### Post by MrWES on 2009-04-01
> **ave2 said:**
> there are so many options when it comes to cd ripping to mp3 software as well as dvd ripping, what would you recommend for each of those- all I wont is something simple, and fast

Check out ABCDE - A Better CD Encoder. It's CLI, but is very very fast.

[http://www.andrews-corner.org/abcde.html]("http://www.andrews-corner.org/abcde.html")

[http://ubuntuforums.org/showthread.php?t=109429]("http://ubuntuforums.org/showthread.php?t=109429")


It's in been around for a long time, and is in the repos. I truly think it's worth a look see.


Bill

---

