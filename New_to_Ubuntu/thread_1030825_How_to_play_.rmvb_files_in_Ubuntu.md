---
title: "How to play .rmvb files in Ubuntu"
date: 2009-01-04
forum: New to Ubuntu
---

### Post by Udavid on 2009-01-04
OMG,I have tried everything I can do to try to play .rmvb files.
to install codec 
to install realplayer 
to install Mplayer 
and install codec needed.
now the only So called improvement is that I can hear the track but no playback.
what Shall I do?

---

### Post by Trist on 2009-01-04
> **Udavid said:**
> OMG,I have tried everything I can do to try to play .rmvb files.
to install codec 
to install realplayer 
to install Mplayer 
and install codec needed.
now the only So called improvement is that I can hear the track but no playback.
what Shall I do?

Hi,
Have you tried installing the w32codecs from Medibuntu?
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by evilkastel on 2009-01-04
you have to install w32codecs if you are in a 32 bits system, or w64codecs if you are on a 64 bits ubuntu. then get mplayer, and that should do it. Altough, playback is not too good on it.
Once you have mplayer WITH the codecs, you have to CONFIGURE it. 
in the audio tab set pulse and in the video tab set x11.
in the codecs tab, choose RealVideo decoder, and for audio in the same codec tab choose FFmpeg/libavcodec audio decoders.
If still it won't play please tell.

---

### Post by Udavid on 2009-01-16
yup  I have to do it after work.
it seems that Ubuntu is not good at playing videos.

---

### Post by Nero147 on 2009-01-16
Hey Udavid,

I just saw your post. I know that because it's not open source it's not as good of an alternative, but the easiest thing for you to do to get your rmvb files to work would be to download and install realplayer for linux from [http://www.real.com/linux](http://www.real.com/linux)

After you install it right click on the file and hit open with real player 11. Here's a link on a walkthrough. [http://maketecheasier.com/how-to-play-rmvb-files-in-ubuntu/2008/12/09](http://maketecheasier.com/how-to-play-rmvb-files-in-ubuntu/2008/12/09)

Also I'm sure that it sounds like old hat and everyone says it, but it's important to remember that ubuntu has no specific problems playing video files, but the rmvb and other real media formats never had the specifications released. So all of the codecs that we have are reverse engineered; this is also why the best option in this instance is to use the closed source player. 

Hope this helps.

---

