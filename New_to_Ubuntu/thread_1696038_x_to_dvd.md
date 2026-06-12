---
title: "x to dvd"
date: 2011-02-26
forum: New to Ubuntu
---

### Post by jadavi on 2011-02-26
Ok so I found a ton of xtodvd converters transmageddon, DeVeDe, Arista Transcoder, ManDVD and none of them will make a playable DVD or atleast not one that will play in my dvd player.  Any ideas on what I may be doing wrong?  I have searched through the forums but found nothing that helped me to the point of having a watchable dvd.  Any help is very much appreciated.

---

### Post by howefield on 2011-02-26
What is the format of the file (the extension) you are trying to convert and what errors are you getting ?

---

### Post by fooman on 2011-02-26
if in the us...make sure that you set devede to "ntsc" and not "pal"

by default,  it may be set to pal....i made a couple of coasters before i realised it. :P

---

### Post by TeoBigusGeekus on 2011-02-26
If you're trying to add subtitles to it, it won't work.
Hardcode them with avidemux and use devede without any subtitles.

---

### Post by jadavi on 2011-02-26
I am trying to convert from .avi or .mpg to whatever format DVD players use.  I have followed MANY tutorials but to no avail.  The one that got the closest was ManDVD but when I try to open the program I get this error message:
Program seems to be running! Else please remove lockfile .run in .mandvd/ directory

Transmageddon just never converts

Arista TRanscoder says it has no DVD Plugin

and DeVeDe makes an .iso and for some reason my dvd player wont play that when i burn it to a dvd.


*** Edit ***
Now Arista give an error message: Conversion of COp Outdvd.mpg to Generic DVD player NTSC failed! Reason: Unable to construct pipeline! could not like lame0 to mux.

---

### Post by GWBouge on 2011-02-26
Maybe a dumb question, but are you burning the IMAGE to DVD, or are you burning the .iso file to a Data DVD?

---

### Post by TeoBigusGeekus on 2011-02-26
Ok, try this then
```
growisofs -Z /dev/dvd -dvd-video /path/to/video/nameofvideo.ext
```
A bit primitive, no menus, animations, etc., but if this doesn't work I don't know what will.

---

### Post by jadavi on 2011-02-26
> **GWBouge said:**
> Maybe a dumb question, but are you burning the IMAGE to DVD, or are you burning the .iso file to a Data DVD?

I feel like an ******* now ... there is an option to burn an iso image to dvd which i assume (correct assumption hopefully) is the proper way to do so.  I will find out soon enough as I am doing so this every instant.

---

### Post by jadavi on 2011-02-26
> **TeoBigusGeekus said:**
> Ok, try this then
```
growisofs -Z /dev/dvd -dvd-video /path/to/video/nameofvideo.ext
```
A bit primitive, no menus, animations, etc., but if this doesn't work I don't know what will.

Dunno what that does but it seemed to have not worked.  It gave me an error message but i figured it out!! 

Thanks all!

---

### Post by jadavi on 2011-02-26
> **jadavi said:**
> I feel like an ******* now ... there is an option to burn an iso image to dvd which i assume (correct assumption hopefully) is the proper way to do so.  I will find out soon enough as I am doing so this every instant.


Well burning the image didn´t work either

ANy other ideas?

---

### Post by TeoBigusGeekus on 2011-02-26
> **jadavi said:**
> Dunno what that does but it seemed to have not worked.  It gave me an error message but i figured it out!! 

Thanks all!
What was the error message?

---

