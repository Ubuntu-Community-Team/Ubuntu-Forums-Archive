---
title: "no sound in the second instance of vlc"
date: 2009-07-17
forum: New to Ubuntu
---

### Post by stonecoldjha on 2009-07-17
Hi everyone,i am recently using ubuntu8.10.....and i switched to kde4.2 yesterday....and i am stuck with a problem......if i have vlc running a video/audio file,and i simultaneously run another multimedia file with vlc,the latter one has no sound.Its only when i close the former one that the other starts playing with sound...........how do i fix this??

---

### Post by NightwishFan on 2009-07-17
That might be a pulseaudio issue. While playing something in VLC run this command in a terminal.
```
speaker-test
```

If you hear white noise then it might not be pulse. If it is a vlc issue, (you can hear vlc and the noise) then run vlc in a terminal by typing:
```
vlc -v
```

See if there is any issues stated in the terminal.

---

