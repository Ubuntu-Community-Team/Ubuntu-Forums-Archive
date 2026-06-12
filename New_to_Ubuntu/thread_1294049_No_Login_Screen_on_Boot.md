---
title: "No Login Screen on Boot"
date: 2009-10-17
forum: New to Ubuntu
---

### Post by fubarific on 2009-10-17
I'd like to preface this with saying I have the magic touch with breaking the linux operating system. 

Short Story:
Whenever I turn on my netbook, it does the whole boot song and dance. However when it gets to the screen where the log-in prompt should be, it doesn't show up. My background is there, the mouse is there... there is no option to log-in.

More Details:
Right before this happened I had ubuntu reloaded onto my netbook, and ran the update manager. During the updates there was a parse error mess up during an install, which I left overnight for my dad to fix in the morning. I never saw what he did with it. So this might be what is causing this. However I'm hoping there is some magic shortcut key I don't know about that will bring back the prompt.

Thanks for any help :)

---

### Post by beastrace91 on 2009-10-18
It sounds like perhaps something might have corrupted during the update - at the screen press crtl+alt+f1 to get to a terminal login - then run ```
sudo apt-get update && sudo apt-get upgrade
``` *Note you will need an internet connection for this - so grab a network cable.

~Jeff

---

