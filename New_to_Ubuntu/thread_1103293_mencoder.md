---
title: "mencoder"
date: 2009-03-22
forum: New to Ubuntu
---

### Post by beswatcher on 2009-03-22
While trying to sort out how to compress a camera video from the huge .mov file to something reasonable sized, I installed mencoder from synaptic. Now I can't even find the application itself, but Mplayer won't run the movie. I get a fatal error message saying 'error opening/initializing the selected video_out device" After first downloading the file from the camera, the file would play in Mplayer. This was before I tried to install mencoder.

Where did I goof at?

---

### Post by Tobi-fp on 2009-03-22
Try sudo apt-get reinstall mencoder

---

### Post by Tobi-fp on 2009-03-22
or you could always try videolanplayer..

Just do "sudo apt-get install vlc"
and then "sudo apt-get install gstreamer-plugi*"
Thats should do the trick.. 

And if you wanna resize, look for some .divx converter

---

### Post by beswatcher on 2009-03-22
*EDIT (HymnToLife): sorry, I clicked the EDIT button instead of the QUOTE one. ^^" Feel free to post your message again.*

---

### Post by beswatcher on 2009-03-22
This goes nowhere. I tried  Synaptic reinstall mencoder and everything is still messed up. Mmplayer will play the original file, but only as frame by frame. Still no mencoder anywhere in the system and Mplayer is now junk!

---

