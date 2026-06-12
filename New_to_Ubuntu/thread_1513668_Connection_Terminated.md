---
title: "Connection Terminated"
date: 2010-06-19
forum: New to Ubuntu
---

### Post by clayman1000x on 2010-06-19
I keep getting a "An Error Occurred: Disconnected: Connection Terminated" every time I play an audio or video file, it will play so far through the media then error. My install is on C Drive but my music and video files are on d drive, they are in my Windows installation. It does this with all file types I have.

---

### Post by sandyd on 2010-06-19
> **clayman1000x said:**
> I keep getting a "An Error Occurred: Disconnected: Connection Terminated" every time I play an audio or video file, it will play so far through the media then error. My install is on C Drive but my music and video files are on d drive, they are in my Windows installation. It does this with all file types I have.
try running
```

pulseaudio -k
```

---

### Post by clayman1000x on 2010-07-08
> **carlee said:**
> try running
```

pulseaudio -k
```
It still didn't work, .avi and mp3 files will start to play but connection error happens within usually 30 seconds. I can't play a whole song.

---

### Post by clayman1000x on 2010-07-09
Bump

---

### Post by clayman1000x on 2010-07-09
How do I move this thread to the Multimedia & Video section of the forum so I don't double thread?

---

### Post by gandaran on 2010-07-09
> **clayman1000x said:**
> I keep getting a "An Error Occurred: Disconnected: Connection Terminated" every time I play an audio or video file, it will play so far through the media then error. My install is on C Drive but my music and video files are on d drive, they are in my Windows installation. It does this with all file types I have.
maybe the d drive is not mounted, try browsing the d drive with nautilus first (this will mount the drive) then start the audio player, see if it works then.
and you do have the codecs installed?

---

### Post by clayman1000x on 2010-07-09
> **gandaran said:**
> maybe the d drive is not mounted, try browsing the d drive with nautilus first (this will mount the drive) then start the audio player, see if it works then.
and you do have the codecs installed?

The first time I tried to play an mp3 format I had to install codecs, same with .avi video files, so codec wise I am fine I think, these file types would not play at all without the codecs. My storage drive icon is on my desktop so doesn't that mean it is mounted. It will play 20 to 30 seconds through any clip and then terminate itself. I have tried various media players and they all do that. Even the Peter Frampton music in my downloads folder won't play correctly.

I just tried again after making sure the "E" drive (my storage drive) was mounted. I tried 2 different MP3 songs and I got this error message:
"pa_stream_writable__sized() failed: Connection terminated"
Audacious played through 3 songs just now and did not have a hiccup at all. I am now going to see if I can tell Audacious to start when I double click a song file. Movie player is the program giving me the problem, I may be able o listen to MP3 with    Audaciou but I can't play an avi with it.

---

### Post by vahnx on 2011-02-21
*bump* occuring on fully updated Ubunut 10.10 x64 laptop when playing video (Cops AVI files) over a Windows 7 x64 network share, using wireless N to connect to my router. Desktop is wired in and video plays fine on my laptop when in Windows or Snow Leopard.

---

