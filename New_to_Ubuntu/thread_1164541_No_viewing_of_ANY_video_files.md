---
title: "No viewing of ANY video files"
date: 2009-05-19
forum: New to Ubuntu
---

### Post by oldrocker99 on 2009-05-19
I'm not exactly a newbie. I needed to do a reinstall. I followed, as I have before, the advice in this thread:

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

NO video file (not .mpeg, nor .avi, nor .wmv) will play for me, in MPlayer, VLC, or exine. In every instance (except for MPlayer, which gives me sound only), the file starts to play, then the player exits.

Anyone have any ideas? This is a new one on me.

8.10 (still, thanks to ATI and the XOrg foundation)](*,)

:guitar:

---

### Post by Zavie A. on 2009-05-19
I'm having your EXACT problem.
I asked the same question earlier.
If I get any promising results ill let you know.

but I found that...If you play songs a music program in the background ex. Rythmbox
the video will play just fine :S

---

### Post by halitech on 2009-05-19
did you install ubuntu-restricted-extras?

```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by oldrocker99 on 2009-05-19
> **halitech said:**
> did you install ubuntu-restricted-extras?

```
sudo apt-get install ubuntu-restricted-extras
```

Yes, already installed...

:guitar:

---

### Post by asmoore82 on 2009-05-19
Try to play a video from a terminal like this:

```
mplayer -vo x11 */path/to/video.avi*
```
(you can click and drag the video to get its path and name typed for you)

If that works, your problem lies with that ATI yet again -
search/ask for how to enable XVideo for ATI cards.

---

### Post by nhasian on 2009-05-19
hold on a tick, i remember this problem description from before.  its your video driver.

I found the post from two weeks ago:

[http://ubuntuforums.org/showthread.php?t=1142863](http://ubuntuforums.org/showthread.php?t=1142863)

---

### Post by oldrocker99 on 2009-05-20
I just discovered that I can play videos just fine if I disable video effects. I have an ATI :mad: X1200, and I'm using the 9.03 drivers. I had used the 9.01 drivers before, and that's what I'm going back to.

---

