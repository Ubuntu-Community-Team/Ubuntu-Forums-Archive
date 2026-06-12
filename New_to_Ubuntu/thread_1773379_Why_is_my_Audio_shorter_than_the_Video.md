---
title: "Why is my Audio shorter than the Video"
date: 2011-06-02
forum: New to Ubuntu
---

### Post by itsols on 2011-06-02
I recorded my desktop on 10.10, saved as ogv file. Plays excellent.

Now, the moment I open the same file on LiVES, the last part of the audio track is truncated. At least a minute's audio is missing!

Is this a bug on LiVES, my OS or is it something I'm not doing correctly?

Now, the strange thing is that, when I open the same ogv file on OpenShot, the VIDEO is shorter. Even the first few seconds is gone.

The only program that opens it correctly so far is PiTiVi. But as I've mentioned on another thread, it takes like a lifetime to render. The last time I checked (last night), even after 7 hours, an 8 minute video hadn't rendered.

I'll just be happy to use LiVES, if the audio issue can be dealt with. It renders the video in an average 30 minutes.

Thanks for any tips!

---

### Post by webofunni on 2011-06-02
If you are able to open that file in one application and not in another, then that is not a problem of the OS. It should be the problem of the application. Did you try extracting audio from the file and mix it in the video editor, to solve the audio issue.

---

### Post by itsols on 2011-06-02
Thanks for your inputs. But I don't think I can AFFORD bringing in another track. Too much overheads :(

This is probably one of the most puzzling issues I've had to work.

I just noticed something. I used PiTiVi and rendered an 8 minute video as FLV in less than 20 minutes. Of course it was SMALL (320 width) and I only snapped the file in one place.

I noticed that as the number of trims/snaps increase, the processing becomes unacceptably slow.

So I guess I'll snap once or twice and then render the file and repeat the cycle until I'm done. Still faster than waiting 30 hours!


What still puzzles me is that my audio track is shorter when I open the ogv file in LiVES. Anyone have an idea ?

---

### Post by 4Orbs on 2011-06-02
I haven't used those programs, but if it is anything like ripping and encoding a dvd then here's my suggestion: If you have audio options to select the format of the audio, I would go with a constant bitrate rather than variable bitrate. Variable bitrates are notorious for encoding mismatching time lines. For example a stereo mix at 160kbs CBR mp3 has acceptable quality for most movies. Rarely is there any distortion during loud passages.

---

