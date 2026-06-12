---
title: "MPEG - DV conversion"
date: 2009-08-28
forum: New to Ubuntu
---

### Post by dan1973 on 2009-08-28
Hello all, does anyone know of a linux based program that will enable me to convert MPEG video to the Mac imovie format of 'DV'?

I have a friend in distress with wedding video!

many thanks

---

### Post by JillSwift on 2009-08-28
> **dan1973 said:**
> Hello all, does anyone know of a linux based program that will enable me to convert MPEG video to the Mac imovie format of 'DV'?

I have a friend in distress with wedding video!

many thanks

I can't find a GUI to do that, but the CLI program "ffmpeg" will do that:
```
ffmpeg -i inputfile.mpg -ac 2 -ar 48000 -s 720x576 -r 25 outputfile.dv
```
-i = Input File Name, -ac = Audio Channels, -ar = Audio Sample Rate, -s = Size, -r = Frame Rate -- I've included the standards for a Sony DV file, which is the industry standard and the one iMovie uses. You can change the frame rate to 30, if your mpeg files match that rate.

If ffmpeg is not installed, it's in the repositories:
```
sudo apt-get install ffmpeg
```Though, IIRC, iMovie knows how to handle mpg files, does it not?

---

### Post by FakeOutdoorsman on 2009-08-28
Or simply (for PAL video):
```
ffmpeg -i input.mpg -target pal-dv output.dv
```
or (for NTSC video):
```
ffmpeg -i input.mpg -target ntsc-dv output.dv
```

---

### Post by dan1973 on 2009-09-02
Thanks for the info, i will file it away for future use as afore mentioned friend ditched his mac for this particular project and used another friend's ................Windows....spit....spit.. machine.

---

