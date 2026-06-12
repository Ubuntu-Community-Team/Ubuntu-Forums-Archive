---
title: "video editor to split .avi files"
date: 2011-04-18
forum: New to Ubuntu
---

### Post by Nagle75 on 2011-04-18
Hello,

I'm using Maverick Meerkat, & I would like to clip a a video segment out of an .avi file so that I can post it on youtube. Would someone please be able to suggest a program w/ a gui, that can do this? Does PiTiVi do this? Thanks for your time!:)

---

### Post by Locke_99GS on 2011-04-18
Yes, PiTiVi does this.

---

### Post by andrew.46 on 2011-04-19
And if you decide to have a look at a commandline program you could do worse than look at avisplit which is part of Transcode.

---

### Post by lovinglinux on 2011-04-19
> **Locke_99GS said:**
> Yes, PiTiVi does this.

As far as I remember, Pitivi re-encodes every output, which most likely isn't really necessary in this case.

Instead use Avidemux. After loading the video file you want, leave the video and audio settings on the left as "copy". This way, the program won't re-encode the video. Then browse the video using the bottom slider to the point where you want to start your edition. Then click the button "Previous keyframe", then click the button "Selection: start". Go forward with the slider to the point you want your clip to end. Click "Next keyframe", then click "Selection: end" button. Now go to the menu and click "File >> Save >> Save Video".

This will save you a lot of time if you need to edit multiple segments and videos, since the process is almost instantaneous, without re-encoding.

You are probably wondering why the "keyframe" buttons steps. That's because you cannot cut an avi anywhere you want, only at keyframes. So when you select the point you want to cut, you need to play with "Previous keyframe" and "Next keyframe" in order to find the best place to cut. Sometimes, depending where you cut, you can't avoid scenes you don't want. In this case you need to use an editor that re-encodes the video like Pitivi, which you can overlap scenes and cut anywhere.

---

### Post by SeijiSensei on 2011-04-19
Mencoder can do this, too.

```
mencoder -o output.avi -ovc copy -oac copy -ss hh:mm:ss -endpos N input.avi
```

This starts copying input.avi to output.avi at starting point hh:mm:ss for N seconds.

---

### Post by lovinglinux on 2011-04-19
> **SeijiSensei said:**
> Mencoder can do this, too.

```
mencoder -o output.avi -ovc copy -oac copy -ss hh:mm:ss -endpos N input.avi
```

This starts copying input.avi to output.avi at starting point hh:mm:ss for N seconds.

Yes, but the OP wants a GUI.

---

### Post by Locke_99GS on 2011-04-19
> **lovinglinux said:**
> As far as I remember, Pitivi re-encodes every output, which most likely isn't really necessary in this case.

Instead use Avidemux. After loading the video file you want, leave the video and audio settings on the left as "copy". This way, the program won't re-encode the video. Then browse the video using the bottom slider to the point where you want to start your edition. Then click the button "Previous keyframe", then click the button "Selection: start". Go forward with the slider to the point you want your clip to end. Click "Next keyframe", then click "Selection: end" button. Now go to the menu and click "File >> Save >> Save Video".

This will save you a lot of time if you need to edit multiple segments and videos, since the process is almost instantaneous, without re-encoding.

You are probably wondering why the "keyframe" buttons steps. That's because you cannot cut an avi anywhere you want, only at keyframes. So when you select the point you want to cut, you need to play with "Previous keyframe" and "Next keyframe" in order to find the best place to cut. Sometimes, depending where you cut, you can't avoid scenes you don't want. In this case you need to use an editor that re-encodes the video like Pitivi, which you can overlap scenes and cut anywhere.

While I'm quite aware that PiTiVi re-encodes, I wasn't aware that there was a working method that did not require re-encoding the video. My video editing experience is limited to hobby use, and only cutting out dead space and poor clips. This is good to know, and very useful for me.

Thanks. ;)

---

### Post by lovinglinux on 2011-04-19
> **Locke_99GS said:**
> While I'm quite aware that PiTiVi re-encodes, I wasn't aware that there was a working method that did not require re-encoding the video. My video editing experience is limited to hobby use, and only cutting out dead space and poor clips. This is good to know, and very useful for me.

Thanks. ;)

You are welcome. Te only annoying thing is the keyframe issue. Sometimes is just better to re-encode anyways.

---

