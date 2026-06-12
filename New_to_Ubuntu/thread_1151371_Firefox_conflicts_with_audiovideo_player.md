---
title: "Firefox conflicts with audio/video player"
date: 2009-05-06
forum: New to Ubuntu
---

### Post by zmike1 on 2009-05-06
When I have firefox open (even minimized to the task panel) I am unable to play video (.avi format from a camera) or audio files (.mp3 from anywhere).

I've tried gstreamer, gxine, VLC, audacious, etc. none of them work unless I quit firefox.  They seem to work otherwise.

Any idea as to the cause of this conflict?

I'm running Hardy on a Dell Inspiron 6400, FWIW.

---

### Post by kelbizzle on 2009-05-07
The same this would happen to me. Although mines had an error message. I would have to kill Pulse Audio every time to get the sound to work.

---

### Post by zmike1 on 2009-05-07
Thanks for the info...
...now:

How do I kill Pulse Audio?
Can Pulse audio be removed so it doesn't need killing?  Will that adversely affect sound?

---

### Post by colau on 2009-05-07
> **zmike1 said:**
> When I have firefox open (even minimized to the task panel) I am unable to play video (.avi format from a camera) or audio files (.mp3 from anywhere).

I've tried gstreamer, gxine, VLC, audacious, etc. none of them work unless I quit firefox.  They seem to work otherwise.

Any idea as to the cause of this conflict?

I'm running Hardy on a Dell Inspiron 6400, FWIW.
Did you install all plugins and codecs needed?

---

### Post by JedV on 2009-05-07
> **zmike1 said:**
> Thanks for the info...
...now:

How do I kill Pulse Audio?
Can Pulse audio be removed so it doesn't need killing?  Will that adversely affect sound?

To kill...

Open the System Monitor (System Menu -> Administration -> System Monitor)

Go to the Processes Tab.  Find Pulse Audio, Right Click, and choose Kill Process

[IMG]http://i23.photobucket.com/albums/b389/CMiki/pulse.jpg?t=1241752545[/IMG]

Your other questions?  Hmmm.

---

### Post by zmike1 on 2009-05-07
Could I open a terminal and type "kill pulseaudio"?  I guess I'll try it and see.

Thanks for the detailed help.

BTW, the problem also exists when i use seamonkey as the browser instead of firefox, FWIW.

---

