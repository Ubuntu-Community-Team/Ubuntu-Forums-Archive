---
title: "No streaming audio"
date: 2011-01-28
forum: New to Ubuntu
---

### Post by ziggiz on 2011-01-28
Never had streaming audio since first install of Ubuntu 8.xx.  Sound card has always worked fine in every application, so long as it's playing a file on the HDD.

Presently I have release 10.04. Kernel Linux 2.6.32-28-generic, GNOME 2.30.2.

Pictures play fine in You-tube, etc, but no audio. Sample audio from record stores and Iceberg radio ([http://www.icebergradio.com/](http://www.icebergradio.com/)) is all missing.

If I stream a You-tube video and save it, then the sound plays fine when I play with VLC or Kaffeine. Same with other streaming movie sites.

When starting Amarok I get error message: "Phonon: KDE's Mulitmedia Library  The audio playback device NVidia CK804 with ALC850 (NVidia CK804 does not work. Falling back to default."  Then it works fine.

Audacious just starts and plays fine with no error message.

Any suggestions?

---

### Post by sydbat on 2011-01-28
Have you enabled the "[Restricted Extras]("https://help.ubuntu.com/community/RestrictedFormats")" "[Medibuntu]("https://help.ubuntu.com/community/Medibuntu")" repositories?

---

### Post by ziggiz on 2011-01-29
Thanks, I didn't have. But some googling and it has been done.

What do I need from these repositories?

---

### Post by fballem on 2011-01-29
> **ziggiz said:**
> Thanks, I didn't have. But some googling and it has been done.

What do I need from these repositories?

wXXcodecs

Where XX is either 64 or 32, depending what installation of ubuntu (either 64-bit or 32-bit) you are running. I generally install from Synaptic (System > Administration > Synaptic Package Manager). It's easy and graphical.

There may be some streaming video that you cannot still cannot see, although the codecs will cover most. If you do need to see these, then I would recommend that you go to fluendo.com and purchase their codecs. These are licensed (not expensive at all). I have had them for three years, and in that time I have not run into a video or audio file that I cannot play.

Hope this helps,

---

### Post by sydbat on 2011-01-29
> **fballem said:**
> There may be some streaming video that you cannot still cannot see, although the codecs will cover most. If you do need to see these, then **I would recommend that you go to fluendo.com and purchase their codecs**. These are licensed (not expensive at all). I have had them for three years, and in that time I have not run into a video or audio file that I cannot play.Completely unnecessary. 

1) Unless you live in the US, you do not have to "purchase codecs".
2) The codecs in the restricted extras repos are the same ones you would "buy".

To the OP - you should also add [Flash-Aid]("https://addons.mozilla.org/en-US/firefox/addon/flash-aid/") to Firefox. It resolves many issues with Flash based websites like YouTube.

---

### Post by ziggiz on 2011-01-29
We are getting somewhere. I installed the codecs and at least now when starting Amarok I don't get the Phonon error message.

However, no audio in youtube, either in Opera or Firefox.

I have added Flash-Aid to Firefox. Still no audio.

When I open a volume control while playing music in Amarok and streaming from Youtube, then the Playback sources are shown as:
System Sounds,mono;
Amarok, Front Left and Front Right,

and that's all. No stream either from Opera or Firefox.

---

### Post by fballem on 2011-01-29
> **sydbat said:**
> Completely unnecessary. 

1) Unless you live in the US, you do not have to "purchase codecs".
2) The codecs in the restricted extras repos are the same ones you would "buy".

To the OP - you should also add [Flash-Aid]("https://addons.mozilla.org/en-US/firefox/addon/flash-aid/") to Firefox. It resolves many issues with Flash based websites like YouTube.

Not quite - Canada would also have the same issue as the US and WMA Lossless is a proprietary microsoft format. That was the reason I had to buy the fluendo codecs in the first place.

I also concur with the recommendation about flash-aid - it is a wonderful tool.

---

### Post by sydbat on 2011-01-29
> **ziggiz said:**
> We are getting somewhere. I installed the codecs and at least now when starting Amarok I don't get the Phonon error message.

However, no audio in youtube, either in Opera or Firefox.

I have added Flash-Aid to Firefox. Still no audio.

When I open a volume control while playing music in Amarok and streaming from Youtube, then the Playback sources are shown as:
System Sounds,mono;
Amarok, Front Left and Front Right,

and that's all. No stream either from Opera or Firefox.OK. Open a Terminal (Applications > Accessories > Terminal) and do two things...

1) Type "alsamixer" (no quotes), hit enter, then check to make sure that nothing is muted. Alsamixer should also allow you to see any other audio cards you may have (F6 I believe).

2) Type "gstreamer-properties". This will open the interface for you to assign what sound card will play any / all gstreamer sounds.

---

### Post by sydbat on 2011-01-29
> **fballem said:**
> Not quite - Canada would also have the same issue as the US and WMA Lossless is a proprietary microsoft format. That was the reason I had to buy the fluendo codecs in the first place.No.

---

### Post by ziggiz on 2011-01-29
1. Nothing was muted.

2. I assigned default output and input plugins to be ALSA, with Device as Default.  Still no streaming sound.

If something were muted, it would show up in the volume control Applications tab as muted. And no stream shows up there.

---

