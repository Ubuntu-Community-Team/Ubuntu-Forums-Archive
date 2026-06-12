---
title: "Rip CD Audio from mounted image (Acetone/Grip)"
date: 2009-04-14
forum: New to Ubuntu
---

### Post by The Bright Side on 2009-04-14
Hi,

I brought my FM Towns versions of the old LucasArts adventures Zak McKracken and Indiana Jones 3 as BIN/CUE images to Canada with me. For those of you who remember those games, the FM Towns CD ROM versions have CD audio tracks that contain the game music (as in, actual CD music tracks). Under Windows, I could just mount an image with Daemon Tools, which would then appear as a new drive, point ScummVM to that virtual drive and play - it would recognize the mounted image as a full CD and play the audio accordingly.

Under Ubuntu, using AcetoneISO, that doesn't work. It mounts an image in an actual folder, and while I can access all the files from the image, the music tracks remain "invisible" to the system.

So I thought, hey let's rip the audio and put it on the hard disk as OGG files, ScummVM will recognize that and play the game correctly. Problem is: Grip, my music ripper, won't detect the mounted image correctly as a CD either. I don't want to burn that thing to CD just to get to the music data!

What can I do? How can I access my music tracks?

Thanks,
M.

---

### Post by gackt on 2009-04-15
1. Sudo apt-get install bchunk
2. open terminal and type bchunk -w "your bin path" "your cue path"
thats it, bchunk will convert it to wav. After that use soundkonverter to convert it into any type you want.

---

### Post by The Bright Side on 2009-04-19
thanks man! :-)

---

