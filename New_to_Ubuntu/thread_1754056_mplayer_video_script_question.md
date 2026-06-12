---
title: "mplayer video script question"
date: 2011-05-09
forum: New to Ubuntu
---

### Post by lance bermudez on 2011-05-09
#!/bin/bash
#update video list
find /media/M*port/torrent -type f \( -name "*" ! -name "video.txt" ! -name "playvideo" \) > video.txt
mplayer -shuffle -playlist video.txt

question is how to i get the video to play at double size? when I just play a video noraml i just click on the vido screen with the mouse and say double size but now i can not do that with the script.

---

### Post by andrew.46 on 2011-05-10
Perhaps try the following addition to the MPlayer section:

```
mplayer [COLOR="Red"]*-xy 2*[/COLOR] -shuffle -playlist video.txt
```

If you want to alter the display size while actually playing you could try using the 'f' key which will toggle fullscreen.

---

### Post by lance bermudez on 2011-05-10
thank you

---

