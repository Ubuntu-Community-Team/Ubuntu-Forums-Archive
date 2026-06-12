---
title: "brasero stopped working"
date: 2011-01-13
forum: New to Ubuntu
---

### Post by albert s on 2011-01-13
up until monday brasero has been working flawlessly for me,
now when I try to burn a video DVD it says its starting to convert files, then a window opens saying ejecting disc and thats it.
it wont do anything.
Ive tried a search but it seems to be related to people on 10.10.
Im using 32bit 10.04 and this is only a recent problem.
thanks.

---

### Post by cariboo on 2011-01-13
Start brasero from a terminal, and make a note of any errors while trying to burn a disk. Paste your errors in your  in your next post.

---

### Post by albert s on 2011-01-13
this is the error log

```
Checking session consistency (brasero_burn_check_session_consistency brasero-burn.c:1741)
BraseroVob called brasero_job_get_action
BraseroVob called brasero_job_get_action
BraseroVob deactivating
BraseroVob called brasero_job_get_action
BraseroVob called brasero_job_get_session_output_size
BraseroVob Output set (AUDIO) image = /tmp/brasero_tmp_TOZQOV.cdr
BraseroVob called brasero_job_get_session_output_size
BraseroVob called brasero_job_get_action
BraseroVob called brasero_job_get_output_type
BraseroVob Got output type (is DVD 1, is SVCD 0)
BraseroVob Creating new pipeline
BraseroVob called brasero_job_get_current_track
BraseroVob called brasero_job_get_audio_output
BraseroVob called brasero_job_tag_lookup
BraseroVob called brasero_job_tag_lookup
BraseroVob Setting ratio 4:3
BraseroVob Linked video bin to muxer == 0
BraseroVob called brasero_job_tag_lookup
BraseroVob Adding AC3 audio stream
BraseroVob Setting AC3 rate to 48000
BraseroVob Setting AC3 bitrate to 448000
BraseroVob Linked audio bin to tee == 0
BraseroVob Linked audio bin to muxer == 0
```

I hope that is what you need.


also if I dont insert a disc it gives me the choice of burning it to an image, should I do that first or is that only adding to the confusion.?

---

### Post by TeoBigusGeekus on 2011-01-13
> **albert s said:**
> ...also if I dont insert a disc it gives me the choice of burning it to an image, should I do that first or is that only adding to the confusion.?
Do the above to create an iso.
If that doesn't work, install DeVeDe to create an iso for your video dvd (you can also create a menu with it).
After you've created the iso file, try
```
growisofs -dvd-compat -Z /dev/dvd=/pathtoiso/image.iso
```
from terminal to burn it. Replace /dev/dvd with whatever is recognized by your system (/dev/cdrw, /dev/sr0, etc.)

---

### Post by albert s on 2011-01-13
all Im getting now is  

```
impossible to link to plugin pads
```

whether I have a disc in or try to burn an iso .
Im going to try DeVeDe ,
off to get some food just now, back soon,
thanks for trying to help.

---

### Post by albert s on 2011-01-13
running DeVeDe now, seems to be working, although quite slow.
should it be this slow,?
I have a core2 duo with 1G ram, albeit a fairly oldish PC,

```
Intel(R) Core(TM)2 CPU          4300  @ 1.80GHz
 
```
thanks again folks.

---

### Post by albert s on 2011-01-14
sorted, well, good enough for me anyway,
thanks for the help folks.
I used DeVeDe to make an image ( .iso )  then used brasero to burn it ,
perhaps not the best method, but simple and straightforward for me to do,
 so its fine for me,  :D

---

### Post by albert s on 2011-01-14
duplicate

---

### Post by albert s on 2011-01-14
sorted, well, good enough for me anyway,
thanks for the help folks.
I used DeVeDe to make an image ( .iso )  then used brasero to burn it ,
perhaps not the best method, but simple and straightforward for me to do,
 so its fine for me,  :D

---

### Post by albert s on 2011-01-14
duplicate

---

### Post by charlescarroll1 on 2011-12-24
I was receiving the same error when I was trying to burn a DVD. I installed DeVeDe and noticed it had to install some extra plugins and thought "maybe Brasero will work after these plugins have been installed", sure enough Brasero works perfectly. :)

---

