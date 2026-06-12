---
title: "MP3 help"
date: 2009-02-04
forum: New to Ubuntu
---

### Post by cowboy7305 on 2009-02-04
Iam having trouble playing mp3s on ubuntu8.1 full install.
have read a lot of things nothing seems to work, the mp3s i am trying to play was down loaded using Frost wire ,it shows up as a mp3 on frost wire but will not play ,have downloaded VlC tells me it can not plat this kind of file ,have loaded sudo apt-get install ubuntu-restricted-extras, also some other codacs that i have read about on This forum ,
Any help out there please 
many thanks

---

### Post by Malalo on 2009-02-04
Then perhaps the file your downloaded is not a MP3 file, or is corrupt.
Can you try playing any other MP3 file ?

---

### Post by cowboy7305 on 2009-02-04
Yes have tryed that still the same 
is there any way of deleting all the files and codacs i have loaded and start again  i may have loaded to much
also when i try to load into vlc it mp3 looks more like a file  icon looks like a bit of paper

---

### Post by AllanPoe on 2009-02-04
Have you installed ubuntu-restrticted-extras?

---

### Post by stoogiebuncho on 2009-02-04
What worked for me were the GStreamer packages.  They're in add/remove, just do a search for them.

Another thing that can sometimes happen is one program will hog your sound card and not let any other programs use it.  Can you try closing down all the programs you have running, and then open vlc again and try once more?

I've heard this doesn't happen as much in 8.10, but it's worth a try anyway.

---

### Post by cowboy7305 on 2009-02-05
When i try to use vcl to play mp3s i get this message 
No suitable decoder module:
VLC does not support the audio or video format "wmal". Unfortunately there is no way for you to fix this.

---

### Post by SuperSonic4 on 2009-02-05
wmal isn't consistent with an mp3 file, all mine say mpga

---

### Post by carml on 2009-02-05
Try to download again the file or try with someone else,because with the G-streamer codecs you should be able to play almost everything you want to.
Maybe this file is corrupted,plus I don't know what ubuntu-extras are,but I repeat you have to install e.g. G-streamer to play mp3.:)

---

### Post by konqueror7 on 2009-02-05
use ```
sudo apt-get autoremove --purge ubuntu-restricted-extras
``` just to be sure,,,then reinstall restricted extras again or gstreamer (i prefer the restricted extras)...

also, some of the files downloaded thru frostwire, some are corrupt or invalid, encountered it many times...now i prefer downloading it thru torrent...

---

### Post by ChrisNZ on 2009-02-05
> **cowboy7305 said:**
> trouble playing mp3s on ubuntu8.1 

Have you tried using another player? how about Amarok in synaptic manager?
I have used this for all but the streaming side and for that I chose Streamtuner for listening and recording.

Why V1c? 

cheers

Chris from NZ  ;)

---

### Post by cowboy7305 on 2009-02-05
Fixed  i had tried to down load  music no bite rate 
just have to watch that in future 
also a lot of music not complete 
many thanks to all who replied

---

