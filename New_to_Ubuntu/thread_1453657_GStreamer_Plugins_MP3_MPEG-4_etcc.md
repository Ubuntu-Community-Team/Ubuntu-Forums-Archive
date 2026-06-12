---
title: "GStreamer Plugins MP3 MPEG-4 etcc"
date: 2010-04-13
forum: New to Ubuntu
---

### Post by skyeric on 2010-04-13
Hey,
I'm trying to copy my itunes library into Rhythm Box but am getting an error along the lines of - Error, additional GStreamer plugins are required to play this file. I've searched GStreamer on Synaptic Package Manager but I'm not really sure exactly what I'm looking for.
Any help appreciated,
Eric

---

### Post by coffeecat on 2010-04-13
The easiest way is to install the metapackage ubuntu-restricted-extras which includes the gstreamer plugins (and other multimedia stuff) that you will need. Be aware that it also includes the package ttf-mscorefonts-installer which installs the Microsoft core fonts. Hardly multimedia, but useful.

---

### Post by skyeric on 2010-04-13
Thanks a lot that was exactly what I was looking for :)
Looks like the rest of its contents are going to be pretty useful too.
Thanks a lot,
Eric

---

### Post by skyeric on 2010-04-13
Hm actually I think I might be getting a bit hopeful but is there anyway to get .m4p files in rhythm box? as in files I've brought of off itunes?
Not really a major issue if not I'm mainly using this for backup purposes so having everything on rhythmbox isn't a major issue but just for neatness sake.
As I said not really a major issue I'm only missing 41 out of well, lots, but if anyone's got any ideas it would be much appreciated.
Cheers,
Eric

---

### Post by coffeecat on 2010-04-13
On the subject of multimedia and so on, another tip if you're new to Ubuntu and want to play commercial DVDs. It's part of my routine when doing fresh installations.

Go to [http://www.medibuntu.org/](http://www.medibuntu.org/) and follow the repository howto for adding the medibuntu repository. Now install libdvdcss2 (needed for playback of encrypted DVDs).

Enjoy!



**Edit:** just saw your last post about m4p files. Do you mean mp4? Because mp4 video files play just fine for me in Ubuntu - or rather MP4 files I've rendered myself in Ubuntu. Could the iTunes files be DRM'd?

---

### Post by skyeric on 2010-04-13
> **coffeecat said:**
> On the subject of multimedia and so on, another tip if you're new to Ubuntu and want to play commercial DVDs. It's part of my routine when doing fresh installations.

Go to [http://www.medibuntu.org/](http://www.medibuntu.org/) and follow the repository howto for adding the medibuntu repository. Now install libdvdcss2 (needed for playback of encrypted DVDs).

Enjoy!


Thanks have done that should be useful, thanks for the advice.

---

### Post by skyeric on 2010-04-13
> **coffeecat said:**
> 
**Edit:** just saw your last post about m4p files. Do you mean mp4? Because mp4 video files play just fine for me in Ubuntu - or rather MP4 files I've rendered myself in Ubuntu. Could the iTunes files be DRM'd?

Here's an example of the file type, copied directly from properties:
MPEG-4 audio (audio/mp4)

I'm reasonably confident its the file type used by itunes when buying tracks from them.

The error message in RhythmBox says: The stream is encrypted and decryption is not supported.
Not sure why it's calling it a stream but yea..

---

### Post by no2498 on 2010-04-13
install smplayer it comes with the 264 codes
terminall tells you how to install it

hope this helps

---

### Post by coffeecat on 2010-04-13
> **skyeric said:**
> The error message in RhythmBox says: The stream is encrypted and decryption is not supported.

That does sound like DRM. Designed to be played only in iTunes - specifically **your** iTunes - I guess.

All I can suggest is to try other video players. The previous poster suggested smplayer which is the Qt Mplayer front-end - hence more suitable for KDE/Kubuntu. Try the vanilla mplayer instead and install either w32codecs (for 32-bit) or w64codecs (for 64-bit) from Medibuntu. That provides some codecs for mplayer but I don't hold out much hope.

Also, try VLC. That's about the best all-round media player going. (You can get it for MacOS and Windows as well.) But I doubt whether it will cope with a DRM'd video.

---

### Post by skyeric on 2010-04-13
> **no2498 said:**
> install smplayer it comes with the 264 codes
terminall tells you how to install it

hope this helps

Does it definitely play this file type (MPEG-4 audio (audio/mp4)) ?
I'm struggling to find a list of supported file types.

---

### Post by coffeecat on 2010-04-13
> **skyeric said:**
> Does it definitely play this file type (MPEG-4 audio (audio/mp4)) ?

We posted simultaneously. Have a look at my last post. Mplayer will play ordinary MP4's but you've got Apple-protected ones there.

---

### Post by skyeric on 2010-04-13
Hm I'm not actually bothered about it enough to start trying loads of different media players, I think you're probably right in that only itunes is going to be able to play it and even then only itunes on computers with my itunes account on them. As I said copying my music was mainly for backup purposes and as I can play 2,500 out of about 2,550 songs I think I'm going to have enough to deal with if my laptop is elsewhere and I'm forced to use it for playing music.
Thanks for solving my problem and helping me elsewhere as well,
Thanks a lot :)
Eric

---

### Post by skyeric on 2010-04-14
If anyone's interested I've found the details on the restricted itunes formats and they definietly cannot be played, heres the link --> [https://help.ubuntu.com/community/RestrictedFormats/iTunesMusicStore](https://help.ubuntu.com/community/RestrictedFormats/iTunesMusicStore)

---

