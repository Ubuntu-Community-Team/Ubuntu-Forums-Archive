---
title: "Single-channel MP3 for Monophonic Recording"
date: 2009-05-23
forum: New to Ubuntu
---

### Post by lhb1142 on 2009-05-23
I sometimes rip CDs the music on which was originally recorded monophonically.

If I rip these discs, using [Sound Juicer] Audio CD Extractor, these CDs are encoded with two channels.

I like to encode at 128 kBps VBR. This gives a fairly small resultant file/folder but it's not as small as I'd like.

Using iTunes on a Windows computer, there is an option to set the ripping option to Single Channel; this encodes at 64 kBps VBR which gives exactly the same audio quality as Two Channel at 128 kBps VBR.

Thus, the resultant Single Channel file/folder is approximately half the size of that encoded as Two Channel.

In the Edit option of Audio CD Extractor, I changed the "channels=2" to read "channels=1" but, when I ripped a mono disc, the size was still about double the size of the same disc ripped in iTunes.

Can anyone tell me what I did wrong and if there is some way to adjust the ripping in Audio CD Extractor to achieve what I want? I have an older Windows computer with the latest version of iTunes so I'm not totally stymied in ripping to Single Channel but I tell you farnkly that I hate using that Windows machine. Once you get used to Ubuntu, there's just no going back. So I would like to be able to accomplish on my Linux computer that which I can accomplish on my Windows one.

I hope there is someone here who can help me with this problem. Thanks.

(Computer is an Acer Extensa 5620-6419, Intel Core 2 Duo T5550, 3 GB DDR2, using Jaunty)

---

### Post by mc4man on 2009-05-24
Haven't used soundjuicer in quite some time so don't know the extent or means to it's settings

If you want the same thing from a mono source as your getting from itunes then it's a cbr encoding at 64k, 1 channel (mono

(what your describing from itunes is not a vbr encoding, more like "good quality (128kbps)" which encodes at 128k for stereo source and 64k for mono source automatically based on the source (mono or stereo

---

### Post by davidsrsb on 2009-05-24
Stereo MP3 usually uses Joint Stereo mode, which is basically mono plus difference. The mono bandwidth is significantly more than half that of the stereo.

I suggest installing lame and its documentation, it's the best mp3 encoder these days

---

