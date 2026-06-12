---
title: "Audio Help"
date: 2011-04-21
forum: New to Ubuntu
---

### Post by Jinumon on 2011-04-21
I figured I'd come here since it's the place for Linux noobs like myself. I just bought myself a MALIBAL Nine X7200, and while it is a beautiful machine, Ubuntu 10.10 (currently my only OS) refuses to play any audio. I installed Ubuntu from a friend's disk on a completely blank laptop. My two audio devices are the Internal Audio Analog Stereo Duplex and an HDA NVidia HDMI Digital Stereo. If you need any more information, I'll do my best to supply it, though you may have to tell me how to do that too. Any help would be appreciated, though I would especially appreciate the step-by-step easy-to-follow help :D 
Thanks a bunch,
Jinumon

---

### Post by viktormas on 2011-04-22
Here's a nice step by step tutorial on setting soundcards in Ubuntu: [http://tinyurl.com/y9t38td](http://tinyurl.com/y9t38td)

---

### Post by Jinumon on 2011-04-22
Tried it once already, no luck so far. I'll probably try it again later, but I'm tired.
Thanks though,
Jinumon

---

### Post by manishraj2011 on 2011-04-22
Do you **hear the start-up sound** that plays before and after login process???

If yes, then your sound-card is fine, you just don't have the **proper audio/video codecs** installed in the system. You can solve this issue by installing **VLC media player**. You can do this by opening the terminal (by going to Applications-->Accessories-->Terminal)  and typing in there :

sudo apt-get update (This will refresh your software package list)

**sudo apt-get install vlc** (This will download and install VLC in your system )

You need a working internet connection for this purpose.

---

