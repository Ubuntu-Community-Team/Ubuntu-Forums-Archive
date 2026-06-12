---
title: "How to close lastfm in Natty?"
date: 2011-05-12
forum: New to Ubuntu
---

### Post by _Smiler_ on 2011-05-12
I know that exiting lastfm sends to tray by default but as I can't access it through the new unity panel I can't figure out how to close it. I'e tried adding all icons (as I want pidgin and other things to appear in the panel too) to the whitelist using a command I found elsewhere but it didn't work. I also tried adding pidgin alone. I've tried "kill lastfm" command which returns: arguments must be process or job IDs
but I know lastfm is the job ID as I can call it using that. At the moment all I can do is stop the music and exit, but I don't like leaving unused processes running. Any help is appreciated!

---

### Post by kostkon on 2011-05-12
*kill* expects a pid, *pkill* is the one you need; thus, to kill the last.fm client you would give
```
pkill last.fm
```
Now about the tray icon problem. You could just disable the tray icon, so that the last.fm app will not close to the tray when you press the close button. To accomplish this, just select *Tools &#8594; Options... &#8594; Account* and disable the *Show application Icon in system tray* option.

If you are using Unity, a good way to hide the app would be obviously to just minimise it to the unity dock :cool:

---

### Post by _Smiler_ on 2011-05-14
Thanks for the reply - laptop crashed meanwhile so I had to reinstall anyway - managed to enable the system tray this time, no idea why it didn't work the last time. Loving this sexy new ubuntu by the way :cool:

---

