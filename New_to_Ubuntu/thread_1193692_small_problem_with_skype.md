---
title: "small problem with skype"
date: 2009-06-21
forum: New to Ubuntu
---

### Post by bubbhasdance on 2009-06-21
Not sure if this is the correct forum for this question, but I'll ask anyway, I suppose.

I am running Skype 2.0.72, and it recognizes my camera and everything perfectly fine (albeit a bit darker than Win Vista, but that's what lamps are for). The only problem is that I have trouble setting up calls.

Whenever I call someone, the call popup screen comes up, but has a "Problems With Audio Playback or Settings" on it. And the person that I called said that a notice that there was "a problem with my sound devices". 

I am able to chat on Skype just fine, so I am wondering what is the problem here. I also used some tips here on how to get my camera to show up in Skype, it involved making a shell script and allowing it to run as an .exe file.

Thanks in advance, guys!

---

### Post by bubbhasdance on 2009-06-21
I believe I was able to solve it by changing audio devices in the Options section of Skype. Thanks guys!

---

### Post by nmaster on 2009-06-23
you may notice a cpu leak because of an issue with pulseaudio.  if you need to remove pulse look at my post here.  it worked for me :)
 [http://ubuntuforums.org/showthread.p...ype+cpu&page=5]("http://ubuntuforums.org/showthread.php?t=1127056&highlight=skype+cpu&page=5")

---

