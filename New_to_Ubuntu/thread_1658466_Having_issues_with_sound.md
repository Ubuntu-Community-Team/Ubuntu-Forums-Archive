---
title: "Having issues with sound"
date: 2011-01-02
forum: New to Ubuntu
---

### Post by skymeyer on 2011-01-02
Hi, I'm completely new to Ubuntu. When I loaded it onto my laptop, I had sound, but for some reason it wouldn't recognize my headphones. I searched for answers to my problem, and tried several solutions, but none of them worked, and after I booted up my computer again I had no sound at all! I'm thinking that one of the "solutions" I tried did this, but I don't really wish to go in and try fixing my previous mistake in fear of causing more problems. I really need help. When I tried to open alsa-mixer in Terminal, I typed in alsamixer and received this message:

cannot open mixer: No such file or directory

when I tried to reinstall alsa-utils using Synapse it failed twice for the same reason; it would try to recover from package failure and then give me this message:

E: alsa-driver-linuxant: subprocess installed post-installation script returned error exit status 2

I'm confused and way in over my head. Anyone have an answer? Also, I'd appreciate it if someone can tell me how to get my laptop to recognize my headphones as well.

---

### Post by earthpigg on 2011-01-02
Could you look at your browser history and show us what 'solutions' you tried that made things worse?

edit: some general advice for sound issues with Linux... Less is More. Be sure to exhaust all possible solutions that do not require 'sudo' or entering your password. It's often something silly, like the relevant channel being muted in alsamixer.

---

### Post by skymeyer on 2011-01-02
I tried this: [http://ubuntuforums.org/showthread.php?t=1624557](http://ubuntuforums.org/showthread.php?t=1624557)
this was editing the text file for alsamixer, but when it didn't work I went back and changed it back to how it was before.

Also tried this: [http://ubuntuforums.org/archive/index.php/t-1460790.html](http://ubuntuforums.org/archive/index.php/t-1460790.html)
this was using some Terminal commands to download and install a file, but it wasn't able to.

So then I tried this: [http://ubuntuforums.org/showthread.php?t=562856](http://ubuntuforums.org/showthread.php?t=562856)
This was when I tried to reinstall alsa-utils

After that I searched for a bit more and came and posted here.

---

### Post by lidex on 2011-01-02
Yeah, you probably borked it but the good news is, it's probably fixable. Need some input though. Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by skymeyer on 2011-01-03
O.k., the information is at:

[http://www.alsa-project.org/db/?f=2c1feb1077c0dac898e6f20bd35fbf0dd290c7e2](http://www.alsa-project.org/db/?f=2c1feb1077c0dac898e6f20bd35fbf0dd290c7e2)

Thank you for helping! I've found this forum extremely welcoming and nice to newcomers :)

---

### Post by lidex on 2011-01-04
Borked, as advertised.
Try this to reset alsa.
```
sudo aptitude --purge reinstall linux-sound-base alsa-base alsa-utils linux-image-`uname -r` linux-ubuntu-modules-`uname -r` libasound2
```
**Reboot.**

---

### Post by skymeyer on 2011-01-04
Hmmm. I typed it in and this is what Terminal said:

sudo: aptitude: command not found

---

### Post by skymeyer on 2011-01-04
Never mind that, I reinstalled aptitude and it worked! Yay!
Thank you very much now my sound is back.
Is there a way to configure alsamixer to get it to recognize headphones? Or should i just leave it how it is?

---

### Post by lidex on 2011-01-04
Try this, in a terminal:
```
echo "options snd-hda-intel model=hp-laptop" | sudo tee -a /etc/modprobe.d/alsa-base.conf
```
Now reboot and check levels in alsamixer, profile, etc. in sound preferences. No joy? Post an updated alsa-info link.

---

### Post by skymeyer on 2011-01-05
It worked! Thank you so much!

---

### Post by lidex on 2011-01-05
You're welcome. Enjoy!

---

