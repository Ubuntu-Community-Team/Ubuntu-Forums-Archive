---
title: "Extracting audio from videos,"
date: 2009-09-22
forum: New to Ubuntu
---

### Post by CaptainMark on 2009-09-22
Anybody know a good bit software for extracting audio from a video,  preferably one with a gui. 
Alternatively someone could recommend a command line program and be prepared to talk to me like an absolute noob, i was told mencoder but googling it confused the heck outta me.

---

### Post by t0p on 2009-09-22
To do this, and lots more, I suggest using **ffmpeg**.  It's a command-line utility, but it's well worth learning how to use it.

An example: If you wanted to strip the mp3 audio from an .flv (flash video) file, you could use ffmpeg like this:

```
ffmpeg -i input.flv -acodec copy -vn output.mp3
```

Note: the '-vn' flag tells ffmpeg to ignore the video. It isn't required for audio only formats such as mp3, but you would have to use it for containers such as ogg or mp4 that can contain both video and audio streams.

To find out more about using ffmpeg to strip the audio from videos (and online streams) check out [this page]("http://linux.byexamples.com/archives/229/extract-audio-from-video-or-online-stream/").  To learn how to use ffmpeg in general, there's a good guide [here]("http://howto-pages.org/ffmpeg/").

---

### Post by ChrT on 2009-09-22
> **t0p said:**
> To do this, and lots more, I suggest using **ffmpeg**.  It's a command-line utility, but it's well worth learning how to use it.

An example: If you wanted to strip the mp3 audio from an .flv (flash video) file, you could use ffmpeg like this:

```
ffmpeg -i input.flv -acodec copy -vn output.mp3
```Note: the '-vn' flag tells ffmpeg to ignore the video. It isn't required for audio only formats such as mp3, but you would have to use it for containers such as ogg or mp4 that can contain both video and audio streams.

To find out more about using ffmpeg to strip the audio from videos (and online streams) check out [this page]("http://linux.byexamples.com/archives/229/extract-audio-from-video-or-online-stream/").  To learn how to use ffmpeg in general, there's a good guide [here]("http://howto-pages.org/ffmpeg/").

Note that mp3 is a **patented, restricted, proprietary codec**, and using and promoting its use harms the natural development of Free Software. To promote Software Freedom and the spirit of GNU/Linux, only use Free audio codecs like Ogg/Vorbis or Flac.

---

### Post by t0p on 2009-09-22
> **ChrT said:**
> Note that mp3 is a **patented, restricted, proprietary codec**, and using and promoting its use harms the natural development of Free Software. To promote Software Freedom and the spirit of GNU/Linux, only use Free audio codecs like Ogg/Theora or Flac.

LOL, yeah, good luck with that!

---

### Post by ChrT on 2009-09-22
> **t0p said:**
> LOL, yeah, good luck with that!

It's simple, instead of

```
ffmpeg -i file.flv -vn file.mp3 
```use

```
ffmpeg -i file.flv -vn -acodec vorbis file.ogg
```or

```
ffmpeg -i file.flv -vn -acodec flac file.flac
```

As far as I know, any audio player in ubuntu that can play mp3 files can also play ogg/vorbis and flac files.

---

### Post by t0p on 2009-09-22
> **ChrT said:**
> It's simple, instead of

```
ffmpeg -i file.flv -vn file.mp3 
```use

```
ffmpeg -i file.flv -vn -acodec vorbis file.ogg
```or

```
ffmpeg -i file.flv -vn -acodec flac file.flac
```As far as I know, any audio player in ubuntu that can play mp3 files can also play ogg/vorbis and flac files.

In my experience, the audio in a .flv file comes in mp3 format.  So when I copy it as an mp3 file, there's no re-encoding involved which preserves the quality.  Re-encoding an mp3 stream to ogg vorbis or flac will affect the quality.  So when I strip the audio from a youtube music video, I keep it as mp3.  To do otherwise would not "promote software freedom", it would just spoil my listening pleasure.

Also, despite the fact that audio players in ubuntu can play ogg vorbis and flac, my portable mp3 player cannot.  I'm not going to buy another player when my current one works fine.  I'll use mp3 format.

As for "the spirit of GNU/Linux": sorry, but I don't buy that particular rms argument.  Ubuntu is "Linux for human beings", don't you know?  Not a gnu in sight!

:p

---

### Post by HarrisonNapper on 2009-09-22
Alternately, one could do both, keeping the mp3 as an option, but giving one the chance to give ogg and flac a try while booting the native OS.

Open source and cloud computing have done a world of wonders for the linux community and the world and any small way we can support that as end-users is, to me, part and parcel to being a part of that community. If someone in your neighborhood was struggling to make a living selling the greatest coffee beans ever made without the quality of the product being beholden to the tried and true methods of bean degradation, wouldn't it be worth a few more extra cents to at least try the coffee from your friend in the community? Especially if you like the coffee and you want to encourage him to keep improving the quality and lowering the price.

---

### Post by ChrT on 2009-09-22
> **t0p said:**
> In my experience, the audio in a .flv file comes in mp3 format.  So when I copy it as an mp3 file, there's no re-encoding involved which preserves the quality.  Re-encoding an mp3 stream to ogg vorbis or flac will affect the quality.  So when I strip the audio from a youtube music video, I keep it as mp3.  To do otherwise would not "promote software freedom", it would just spoil my listening pleasure.

Also, despite the fact that audio players in ubuntu can play ogg vorbis and flac, my portable mp3 player cannot.  I'm not going to buy another player when my current one works fine.  I'll use mp3 format.

As for "the spirit of GNU/Linux": sorry, but I don't buy that particular rms argument.  Ubuntu is "Linux for human beings", don't you know?  Not a gnu in sight!

:p

Wrong, there is no re-encoding to flac either, I've just tried ffmpeging a .flv file fresh off youtube and it was converted in an instant. Also, which part of "lossless" did you not understand?

And how is your (poor) choice of portable audio player in any way related to this thread? In any case, if it's supported, try putting [Rockbox]("http://www.rockbox.org/") on it, that supports Free audio codecs and standards.

Also, try removing the GNU GRUB, core libraries and coreutils from your ubuntu GNU/Linux software distribution, and have fun attempting to use "ubuntu" without those.

---

### Post by HarrisonNapper on 2009-09-22
Okay, before this goes any further, keep a few things in mind:
a. this is not related to the question of the original poster
b. this is becoming somewhat emotionally driven, which is fine, I think a lot of people on these forums can appreciate both sides of this, but this is not the place
c. this is the Absolute Beginner forum, so anything you say, personally driven though it may be, can reflect on the entire Ubuntu community to new users. Please set the expectation that issues will be solved completely, efficiently, and courteously.

Also, link me to the new thread. I'm definitely interested to participate.

---

### Post by MrWES on 2009-09-22
> **CaptainMark said:**
> Anybody know a good bit software for extracting audio from a video,  preferably one with a gui. 
Alternatively someone could recommend a command line program and be prepared to talk to me like an absolute noob, i was told mencoder but googling it confused the heck outta me.

Avidemux will extract from an avi and/or mp4 file. Open the video file; under Audio, choose mp3(lame) and then click configure and choose your settings; stereo, quality, bitrate, etc. Now from the "Audio" drop down menu, choose save; give it a name, myfile.mp3 and save. Depending on the size of the file, it could take just a few minutes to several.

Bill

---

### Post by t0p on 2009-09-22
> **ChrT said:**
> Wrong, there is no re-encoding to flac either, I've just tried ffmpeging a .flv file fresh off youtube and it was converted in an instant. Also, which part of "lossless" did you not understand?

And how is your (poor) choice of portable audio player in any way related to this thread? In any case, if it's supported, try putting [Rockbox]("http://www.rockbox.org/") on it, that supports Free audio codecs and standards.

Also, try removing the GNU GRUB, core libraries and coreutils from your ubuntu GNU/Linux software distribution, and have fun attempting to use "ubuntu" without those.

Aww, did I upset you?  Sorry.  Didn't mean to hurt your feelings.

Tell you what though: no matter how much you bang on about ogg vorbis and flac, the majority of ubuntu users will continue to use mp3.  No point getting all worked up about it.

Oh yeah, and it's not "GNU/Linux".  It's Linux.

---

### Post by cariboo on 2009-09-22
This thread is about extracting audio from a video not which codec is better. The op's question has been answered. This thread is closed.

---

