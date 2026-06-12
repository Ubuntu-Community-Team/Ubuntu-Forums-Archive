---
title: "Remove hardcoced subtitles."
date: 2010-03-01
forum: New to Ubuntu
---

### Post by Julita on 2010-03-01
Hi! I need to remove subtitles from .avi. Is there a way to do it? I know that VirtualDub does it with delogo filter, are there any counterparts in Linux? I don't mean cropping the image, I mean "extracting" subtitles... i have been advised to read man for mencoder, but I have not found the relevant info, maybe I haven't looked for it as thoroughly as I should have!!! Any help would be greatly appreciated.

---

### Post by gsmanners on 2010-03-01
I highly doubt you can remove the subtitles from anything that's hardsubbed. Even VirtualDub's DeLogo can only remove alpha-blended logos without destroying the image underneath.

Of course, there's really nothing stopping you from installing Wine and using VirtualDub (or Avisynth or any number of Windows video editing tools).

---

### Post by skymera on 2010-03-01
Are you sure they're def hardcoded?

In VLC click the Video menu and then click Subtitles Track and click "0" or none.
Does that work?

---

### Post by Julita on 2010-03-01
Thank you for the answers! I wouldn't need wine because I have dual-boot with Windows, and I was particularly interested in Linux way to cope with this problem. Besides, the latest VirtualDub wouldn't run via wine in my system (not sure about earlier versions.) Since I have not seen the video, I assumed that the subtitles covered the image. In reality, they were attached to it in the form of a black box with a text (like vertical extension,) so I just have to crop the video with Avidemux. I have set the perfect parameters, now I have to wait until it is finished. In the end, it was really challenging to look for the answer; I have found several Windows-ways to do it, and all of them are time-consuming. I really have no idea why people would hardcode subtitles to .avi. .mkv is the best container for video+subtitles. Not many DVD-players read it, though, but there are always conversion methods. I think it is better to keep subs in a separate folder for .avi... Besides, it is easier to embed in .avi than remove, as it turns out ;)

---

