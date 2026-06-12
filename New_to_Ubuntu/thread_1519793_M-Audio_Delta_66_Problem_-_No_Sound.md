---
title: "M-Audio Delta 66 Problem - No Sound"
date: 2010-06-28
forum: New to Ubuntu
---

### Post by NicKardasis on 2010-06-28
Hi guys.I'm new to Ubuntu and Linux generally.I have a m-audio delta 66 PCI sound card installed on my pc but i cannot configure it properly.I think that i have configured it right (alsa mixer and envy24) but no sound at all.I disabled the on-board sound card and delta 66 is the default one now, but still something is wrong.Can someone please help me?I installed Ubuntu a few days ago and still i cannot solve this problem.Please help!!!

---

### Post by okplayer02 on 2010-06-30
run the command 

```
lspci
```
 so we can know the exact chipset and do u know if you have Alsa or Pulseaudio installed on your machine? The two work very differently from each other.

---

### Post by NicKardasis on 2010-07-03
Hi and thanks for the reply.I ran the command and i can't see anywhere the pci sound card (delta 66).I can see only the multimedia audio controller which is the Envy24 (from alsa tools).The chipset is ICE1712.I use alsa and i surely don't have pulse installed.So the pci sound card isn't really recognized or there is onother problem?

---

### Post by NicKardasis on 2010-07-03
Sorry,my mistake.I have pulse audio installed but i don't know how to configure it.

---

### Post by stmiller on 2010-07-04
```

sudo apt-get remove pulseaudio

```

Then reboot. Should work ok then.

Envy and pulseaudio don't work well together.

---

### Post by NicKardasis on 2010-07-04
It worked!!!Thank you very much guys,that was a great help.I removed only the pulse audio and everything works now.

---

### Post by xigen on 2011-03-21
This worked for me too!

Ubuntu 10.10
Delta 66

Many thanks.

---

