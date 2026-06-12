---
title: "Install Help..."
date: 2010-12-17
forum: New to Ubuntu
---

### Post by gallifrey97457 on 2010-12-17
Hi There,

Yes I am new... and am lost...

I am trying to Ubuntu 10.10 on my laptop 
Dell Studio 1558
-4 Gigs, I7 cpu Q720, Ati 5400 video card.

The live cd works fine, and I can use it when I install it, after the install completes, and I reboot Ubuntu loads and then the Ubuntu purple page comes up for a few seconds then disappears and the screen goes black.  I can wait for ever and nothing comes back, however when I hit the power button to turn the laptop off, guess what the purple screen comes back for a second or so then the laptop shuts down.

Can someone point me in a direction on how to fix this?

Thank you for taking the time to read the question.

---

### Post by MooPi on 2010-12-17
When the computer is booting hit the shift key to enter grub boot loader.From grub select recovery mode and then select root console. From the console do an update ```
apt-get update
``` ```
apt-get upgrade
```
After it completes reboot to see if this corrects your issue.

---

### Post by albert s on 2010-12-17
you may need to be plugged into the internet for this though.

---

### Post by gallifrey97457 on 2010-12-17
So I did the update and it still does the same... Hmmm what happens is

I select Ubuntu.... then it loads the purple screen comes on... then it goes off... when I hit the power button then it comes back on and shuts down..  

Any other ideas? And thanks for the help :)

---

### Post by MooPi on 2010-12-17
Follow the instructions from this link and post the results back here.[http://bootinfoscript.sourceforge.net/]("http://bootinfoscript.sourceforge.net/")

---

