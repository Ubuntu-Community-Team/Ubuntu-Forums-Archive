---
title: "Headphones work but sound still comes from speakers"
date: 2008-12-06
forum: New to Ubuntu
---

### Post by Dirtbead on 2008-12-06
I have an ASUS M2N-VM DVI motherboard running ubuntu 8.10. Sound plays fine out of my speakers but when I plug in my headphones I get sound through both my headphones and my speakers which is very annoying. Can somebody please tell me what is going wrong. All help is appreciated.

---

### Post by phidia on 2008-12-06
See if the [thread here]("http://ubuntuforums.org/showthread.php?t=827284&highlight=jack+sense") has the answer for you.

---

### Post by Dirtbead on 2008-12-06
Nope still the same problem.

---

### Post by Duck2006 on 2008-12-06
If this is a laptop, is there not a key on the keyboard that you press to turn of the speakers of with.
ie Fn+(a key, one of the f-keys)

---

### Post by Dirtbead on 2008-12-06
It's a desktop pc.

---

### Post by pp. on 2008-12-06
Double click on the volume control (on screen top right if everything's left at the default settings), go to page "Switches" or similar, check "Headphone jack sense".

---

### Post by Dirtbead on 2008-12-06
There is a switches tab but it has no "headphone sense" just "headphones" which I have ticked.

---

### Post by Duck2006 on 2008-12-06
> **pp. said:**
> Double click on the volume control (on screen top right if everything's left at the default settings), go to page "Switches" or similar, check "Headphone jack sense".

On my systen it is "Double click on the volume control (on screen top right) Click Edit >> Preferences and do it from there.

---

### Post by Dirtbead on 2008-12-06
It just has preferences on 8.10 not edit.

---

### Post by phidia on 2008-12-06
You could try and install "jack-tools" through synaptic or apt.

---

### Post by Dirtbead on 2008-12-06
Might just go back to windows xp. Ubuntu is very buggy with things that should work out of the box.

---

### Post by malathion on 2008-12-06
Install pavucontrol. If this is a problem with PulseAudio, pavucontrol will give you options for how to choose where sound streams will be directed. I'm not sure if this is a problem with PulseAudio or not, but you can try it out. It has been a godsend for me with my dual soundcard setup. Good luck.

---

### Post by Dirtbead on 2008-12-06
I have tried that and no luck. Going to boot a live version of 7.10 and see if that works. Still no luck with an older version. Let me explain my problem a bit more. I have speakers plugged in via the back audio panel on my motherboard when I plug headphones into the front audio panel I get sound in both headphones and speakers. I need just the sound to come through my headphones when plugged in and not both.

---

### Post by malathion on 2008-12-06
I think I am understanding a bit better now. You have one onboard audio device that sends output to two separate sockets. Indeed that is not a problem that would be solved by pavucontrol, but by something in the audio driver. It's too bad that the manufacturer of this device does not provide Linux drivers for it. Nevertheless I'm sure a solution to this exists, but I'm not knowledgeable enough to guess what it might be. Good luck, and please post back here if you find an answer!

---

### Post by Dirtbead on 2008-12-08
Just installed ubuntu 8.4.10 and suprise suprise it works! I am just running updates now to see if it still will work after. It seems ubuntu 8.10 is far more buggy than I first thought.

---

