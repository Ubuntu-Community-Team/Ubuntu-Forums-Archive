---
title: "Rhythmbox issue..."
date: 2010-02-16
forum: New to Ubuntu
---

### Post by Matbenjen on 2010-02-16
Finally made the jump from windows to Ubuntu :-)

I know this is a fairly common problem, but all the other threads I've looked at don't seem to help. Trying to set up my media library in Rhythmbox, which unfortunately contains a few .wma files, and I keep getting the "search for suitable plugin?' message, followed by the 'no packages with the requested plugin found' message.

So far I've installed the restricted extras, medibuntu, w32 codecs, and probably a few other bits and bobs that I can't remember the name of off the top of my head.

I know I could convert all the .wma files, but I know at some point I'll want to play other people's music through my computer, some of which might be wma, so I reckon in the long run it'd be best to get this sorted. 

Any ideas?

---

### Post by HarrisonNapper on 2010-02-16
Double check that the w32codecs are installed. Also, if you don't have it, install ffmpeg and run it from terminal--it will show you all of the supported codecs for both decoding and encoding (you would want availability for decoding). Make sure you run ffmpeg from a terminal, though.

Cheers.

---

### Post by kostkon on 2010-02-16
Remove from your library any files that aren't songs or images.

---

### Post by zeroseven0183 on 2010-02-16
Although I do have images (album artwork) together with my songs, they're played in Rhythmbox with no problem.

How about checking if those WMA files are "locked" (or read-only)?

---

### Post by wojox on 2010-02-16
See if you have:

```
gstreamer0.10-ffmpeg
```

---

### Post by Matbenjen on 2010-02-17
Cheers for your suggestions guys. W32 codecs are definitely installed, as is ffmpeg, but still no luck. 

The files aren't locked (in permissions it says 'read and write').

Don't think it's anything to do with non-audios files, even when I try to open a file in isolation, it won't have any of it. Also discovered that it's not just rhythmbox, vlc won't play them either (which is odd, because my version of vlc on windows had no issues). Vlc gives me the (not too encouraging) message   p, li { white-space: pre-wrap; }  [COLOR=#FF0000]
[/COLOR]
[COLOR=#FF0000]"No suitable decoder module:[/COLOR]
 [COLOR=#000000]VLC does not support the audio or video format "wmal". Unfortunately there is no way for you to fix this."[/COLOR]

[COLOR=#000000][/COLOR]
[COLOR=#000000]Harrison, your suggestion of running ffmpeg through terminal to get a list of supported codecs for encoding/decoding - what command do I enter to do this? And how do I then use the list to help me out? Sorry to need everything spelling out!
[/COLOR]

---

### Post by Matbenjen on 2010-02-17
Also, don't know if this is relevant, but wmv files play just fine in movie player and vlc. So frustrating!

---

### Post by HarrisonNapper on 2010-02-18
Yeah, you definitely don't have the codec to decode wmav. As for the ffmpeg command, can't remember off hand, but type in ffmpeg --help and it will give you a list of commands.

Cheers.

---

