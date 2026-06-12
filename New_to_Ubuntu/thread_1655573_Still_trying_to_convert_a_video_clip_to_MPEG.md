---
title: "Still trying to convert a video clip to MPEG"
date: 2010-12-29
forum: New to Ubuntu
---

### Post by tweedmeister on 2010-12-29
I'm real new at Ubuntu. I love it, but I'm lousy with Linux. About a year ago somebody gave me a DVD recorded at a concert that I participated in. I found some Ubuntu editing software (Avidimux, I think) and edited out the clips I wanted. But the clips saved as AVI files. They have no extensions (like "clip.avi," for example), but looking at properties they each say "Type: AVI video/x-msvideo." 

I would like to upload them to YouTube, but need to convert them to something that YouTube and Facebook accept.

Somebody said that I needed to bring up a term window and type:
"ffmpeg -i input.avi -target ntsc-dvd -aspect 16:9 final.mpg" 
("input.avi" being the name of the clip + .avi)

Whenever I do this, all I get is "file not found". I'm in the right directory, but it the command can't see the file. I've tried both with and without ".avi".Suggestions? Anyone know how to save an AVI into a different format? I have the clips saved both on the desktop and in "videos."

Thanks in advance for help.

Mike T.

---

### Post by cariboo on 2010-12-29
IF you are in the same directory us a ./ before the file name eg:

```
ffmpeg -i ./input.avi -target ntsc-dvd -aspect 16:9 final.mpg
```

using the correct name of the file of course.

---

