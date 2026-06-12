---
title: "VLC window too large for me to resize"
date: 2010-03-30
forum: New to Ubuntu
---

### Post by schlitz100 on 2010-03-30
I got an error trying to open an archived video file and since then when I open vlc it's at full screen when not in full screen mode and I cannot resize it to make it smaller. I have tried holding alt to move the window and alt-f7 but none worked. Is there a way to make ubuntu forget this current window setting?

---

### Post by lotharmat on 2010-03-30
Can you right click on the main window --> Video --> Zoom then set it smaller?

---

### Post by schlitz100 on 2010-03-30
when I do that nothing happens on screen.

---

### Post by KIAaze on 2010-03-30
Try the following:
```
mv ~/.config/vlc{,.bak}
mv ~/.cache/vlc{,.bak}
```
(should reset all vlc settings to default)

If you don't want to reset vlc settings, you can try the various command-line options:
```
vlc --help
```
ex:
```
Video
-f, --fullscreen, --no-fullscreen  Fullscreen video output (default disabled)
Window properties:
--aspect-ratio <string>    Source aspect ratio

```

---

### Post by schlitz100 on 2010-03-30
thanks I was about to reinstall vlc this saved some time.

alt-middleclick didn't work either i think it was really screwed up.

---

