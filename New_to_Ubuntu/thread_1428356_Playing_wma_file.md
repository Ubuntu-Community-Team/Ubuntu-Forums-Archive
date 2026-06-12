---
title: "Playing wma file"
date: 2010-03-12
forum: New to Ubuntu
---

### Post by dunbrokin on 2010-03-12
I am trying to play a wma file...with no luck...so I thought I would convert it to an MP3 file to see if I could play that....this was the error I got from VLC....where do I go from here?


Streaming / Transcoding failed:
It seems your FFMPEG (libavcodec) installation lacks the following encoder:
MPEG Audio layer 1/2/3.
If you don't know how to fix this, ask for support from your distribution.

This is not an error inside VLC media player.
Do not contact the VideoLAN project about this issue.

---

### Post by howefield on 2010-03-12
Have you got w32codecs installed ? (w64codecs if your install is 64 bit)

---

### Post by chaanakya_chiraag on 2010-03-12
Hmmm...basically, you lack the mp3 codecs.  Can you try this command (It will install LAME, which should fix your mp3 woes):
```
sudo aptitude install lame
```

---

### Post by NightwishFan on 2010-03-12
Add the medibuntu repository to get multimedia support for such formats.
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by chaanakya_chiraag on 2010-03-12
And for wma files, do the following:
1) Go to Software Sources and make sure everything is checked
2) Go to the second tab and click Add
3) Enter in "deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) karmic free non-free" in to the line, entering it without quotes
4) Hit the "Add Source" button and then hit the Close button.  A window should pop up...hit Refresh (or something similar) and let it exit on its own.
5) Go into synaptic and search for w32codecs
6) Mark it for installation and hit "Apply"
7) You should be good to go!

---

### Post by mc4man on 2010-03-12
as far as the ffmpeg no mp3 deal read here
[http://ubuntuforums.org/showthread.php?t=1117283](http://ubuntuforums.org/showthread.php?t=1117283)

As far as vlc and wma, you can only decode wma2 with the repo and or ppa vlc builds, for wma3 or wmal you must build your own

---

### Post by era86 on 2010-03-12
[https://help.ubuntu.com/community/RestrictedFormats/](https://help.ubuntu.com/community/RestrictedFormats/)

---

### Post by dunbrokin on 2010-03-12
> **howefield said:**
> Have you got w32codecs installed ? (w64codecs if your install is 64 bit)

Yes...had already been installed.

---

### Post by dunbrokin on 2010-03-12
> **chaanakya_chiraag said:**
> Hmmm...basically, you lack the mp3 codecs.  Can you try this command (It will install LAME, which should fix your mp3 woes):
```
sudo aptitude install lame
```

Still cannot play it....did not get the error again message again though.

---

### Post by dunbrokin on 2010-03-12
> **chaanakya_chiraag said:**
> And for wma files, do the following:
1) Go to Software Sources and make sure everything is checked
2) Go to the second tab and click Add
3) Enter in "deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) karmic free non-free" in to the line, entering it without quotes
4) Hit the "Add Source" button and then hit the Close button.  A window should pop up...hit Refresh (or something similar) and let it exit on its own.
5) Go into synaptic and search for w32codecs
6) Mark it for installation and hit "Apply"
7) You should be good to go!

Nope, installed Medibuntu etc....seems to play with VLC not with MPlayer...but no sound.

---

### Post by mjitkop on 2010-03-12
Is it a protected WMA file with DRM?

---

### Post by dunbrokin on 2010-03-12
> **era86 said:**
> [https://help.ubuntu.com/community/RestrictedFormats/](https://help.ubuntu.com/community/RestrictedFormats/)


Was already installed...but still no sound....seems to play though.

---

### Post by dunbrokin on 2010-03-12
> **mjitkop said:**
> Is it a protected WMA file with DRM?

How would I work out if that is the case....

---

### Post by dunbrokin on 2010-03-12
Codec is WMA Version 8

---

### Post by mjitkop on 2010-03-12
If it's a protected file with DRM coming from Windows, I don't think it is (legally) possible to play it.

However you said that VLC seems to play it albeit without sound. Now that I think of it, if it was a protected file, I think VLC would tell you that.

Is there another WMA file you can try and you know works?

---

### Post by dunbrokin on 2010-03-12
Having followed all the above, I again tried to get VLC to convert wma to mp3...it gave the message "streaming" and ran and far as 47 secs out of about 35mins and then stopped. I do not have any other wma files on my PC...can anybody suggest one that should work?

---

### Post by dunbrokin on 2010-03-12
Here is the link to the original

http://webcastingplayer.corporate-ir.net/player/playerHOST.aspx?c=69964&EventId=2757903&StreamId=1451518&IndexId=&TIK={7b1a17e8-9a33-4d61-9b5d-afa6800e3841}&RGS=3

---

### Post by NightwishFan on 2010-03-12
The link at that locations plays for me using the totem mozilla plugin. I am using Debian unstable, and have the multimedia repository enabled. (I have to click the little windows icon in the player correct?) Edit: My ffmpeg version is 5:0.5.1+svn20100311-0.0

---

### Post by mjitkop on 2010-03-12
Ohhhhh it's a streaming WMA. It can't be protected. I thought it was just a file that you had on your computer.

Sorry but I do not have any other suggestions other than what's already been said. :(

---

### Post by dunbrokin on 2010-03-12
> **mjitkop said:**
> Ohhhhh it's a streaming WMA. It can't be protected. I thought it was just a file that you had on your computer.

Sorry but I do not have any other suggestions other than what's already been said. :(

I have both...I asked them to send me the file as I could not play it on line.

---

### Post by dunbrokin on 2010-03-12
> **NightwishFan said:**
> The link at that locations plays for me using the totem mozilla plugin. I am using Debian unstable, and have the multimedia repository enabled. (I have to click the little windows icon in the player correct?) Edit: My ffmpeg version is 5:0.5.1+svn20100311-0.0

Can't seem to find a totem plug in on the Mozilla FF add-on page.

---

### Post by NightwishFan on 2010-03-12
It is already installed on Ubuntu I am sure. Did you follow the instructions to add the medibuntu repository? If so then run this command:
```
sudo aptitude update && sudo aptitude install gstreamer-ffmpeg
```

---

### Post by dunbrokin on 2010-03-12
Hmmm!...no sound from MP3 files either....best restart my machine and see what happens.

---

### Post by NightwishFan on 2010-03-12
If it can play with Totem and no warning message appears, even if no sound comes out, then it might just be a sound issue. Make sure it is not muted in the program and the applet.

---

### Post by dunbrokin on 2010-03-12
Hmmmm, I have 2 IDs on my PC...if one has recently played and audio file, then the other one is unable to play one until the machine is restarted. Control does not pass automatically from one ID to the next as far as audio is concerned.

This wma file works perfectly now after a restart...thanks to all who made suggestions.

---

