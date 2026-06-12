---
title: "Serious Media Problem"
date: 2011-04-05
forum: New to Ubuntu
---

### Post by Bob Abouille on 2011-04-05
I'm running Ubuntu 10.10 on a Dell Inspiron. For video adapter it says "Intel Chipset". I have g-stream codecs installed for divx, xvid, mp3, quicktime and more. I recently installed everything in Synaptic that had the word gstream in it, and this problem persists:

Whether audio or video, media will play perfectly for 10-30 minutes before the seek bar starts skipping back and forth and it does not stop. The result is the playback jumps back 2 seconds, then ahead 5 seconds, then back 3 seconds, and so on, and it does not stop. Once the skipping starts, it will happen for all files, as soon as they start to play, for the rest of the Ubuntu session. Needless to say, I am unable to play any media, even streaming media, in Ubuntu.

Why would it play the file correctly for 15 minutes and then stop working? Every single time. In addition to the time travel, the audio quality goes down hill as soon as it starts skipping, sounding like a fading FM signal.

Everything works in Windows. Is there another codec pack available besides gstream? Any other ideas or suggestions? Thanks, Bob

---

### Post by Quintilian on 2011-04-05
what media program are you using? For video, I recommend using VLC. all you need to do is type:

sudo apt-get install vlc

in a terminal to install it. vlc comes with all the codecs/decoders that you'll most likely need, so chances are it'll play whatever files you need it to. and i've never had the issue you've described with vlc. vlc will play audio or video, but i just use rhythmbox for that.

---

