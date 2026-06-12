---
title: "No sound with virtualbox"
date: 2009-02-01
forum: New to Ubuntu
---

### Post by eilios on 2009-02-01
After a bit of tinkering, I was able to figure out how to get ZSNES to work, among other things. Unfortunately, when I am trying to play Chrono Trigger there is no sound, and even though I installed the virtualbox drivers, there is still no sound.

---

### Post by NeuralEskimo on 2009-02-01
I'll start by asking this simple questions -- sorry if that offends you.

1) Have you turned sound support on for your virtual machine? This is not done by default. Select your virtual machine, and click settings. Select Audio and check the enable check box. Finally, select the proper "Host Audio Driver", which is mostly likely ALSA or Pulse Audio.

2) Are the sound drivers installed and configured for the guest operating system? 

Let me know if this works or doesn't work. If not, we will continue troubleshooting.

---

