---
title: "vlc problem"
date: 2009-11-10
forum: New to Ubuntu
---

### Post by tedlee on 2009-11-10
I have been using ubuntu starting from version 8 then 9.04.
vlc works perfectly for me.
I upgrade my system to 9.10, with vlc 1.0.2 yesterday.
When I play a movie (.avi) with .srt subtitle, there is not subtitle at all shown by vlc.
Subtitles are normal if I switch to mplayer.
Can anyone help?

---

### Post by celtic426 on 2009-11-10
Does it work if you go to "File-->Advanced Open File" and then select the subtitle there?

---

### Post by tedlee on 2009-11-10
No.
I have tried to load the subtitle file explicitly, no luck!

---

### Post by celtic426 on 2009-11-10
I think I got it.  
Go into Tools then Preferences.  Click on Subtitles and OSD.  Then in the subtitle encoding area, change the "Default Encoding" to the one that fits your needs.

---

### Post by andrew.46 on 2009-11-10
Hi tedlee,

> **tedlee said:**
> When I play a movie (.avi) with .srt subtitle, there is not subtitle at all shown by vlc.

The easiest way is to have the srt file in the same location as the avi, i.e. in the same directory, and then either vlc or MPlayer will use it *automagically*. This does not work?

Andrew

---

