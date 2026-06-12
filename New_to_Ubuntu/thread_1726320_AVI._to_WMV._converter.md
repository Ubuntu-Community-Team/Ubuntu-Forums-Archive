---
title: "AVI. to WMV. converter ??"
date: 2011-04-11
forum: New to Ubuntu
---

### Post by haggardtechno on 2011-04-11
Hello everyone, I recently made the switch from windows to Ubuntu 10.10 , and I was wondering what software I should use to convert my avi. movies into wmv. movies so I can burn them off and play them on my 360. Any help as to what program and how to get it, would be much appreciated, thanks.

---

### Post by papibe on 2011-04-11
You can use ffmpeg, but there's same legal issues. Also, it doesn't make any sense since Xbox 360 can play most AVI files (read it [here]("http://www.afterdawn.com/guides/archive/what_will_xbox_360_play.cfm")).

Does your 360 don't play your AVI movies? If not, maybe it's a codec issue. I'm sure you can use ffmpeg to change the codec to something playable like DivX or XviD

Regards.

---

### Post by wolfen69 on 2011-04-11
Winff is a good GUI app for this.

---

### Post by seawolf167 on 2011-04-11
You could use ffmpeg for this

```
ffmpeg -i video.avi -vcodec wmv2 video.wmv
```

Of course if you don't like the output you can add additional switches for bitrate, etc.

---

### Post by haggardtechno on 2011-04-11
Awesome, thanks so much guys. Also [papibe]("http://ubuntuforums.org/member.php?u=774785") was right. I originally read that the 360 wouldn't read avi.'s , but it certainly does, hah. Thanks again.

---

