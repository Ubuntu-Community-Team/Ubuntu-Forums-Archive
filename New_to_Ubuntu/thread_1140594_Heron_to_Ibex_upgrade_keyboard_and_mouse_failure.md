---
title: "Heron to Ibex upgrade keyboard and mouse failure"
date: 2009-04-27
forum: New to Ubuntu
---

### Post by Ragged on 2009-04-27
Hi, I just started using Ubuntu about six months ago, and I've been using heron the whole time, works great. I tried yesterday to upgrade to Ibex and then to Jaunty(planned to) but after installing Ibex, upon restart, my keyboard and mouse no longer work. what should I do? I assume I can revert to a prior state, but can I upgrade or is my computer trapped in Heron?

---

### Post by Kareeser on 2009-04-27
Odd. Unless there is a hardware problem, I'm assuming you have keyboard input during the boot-up process.

Press ESC at the Grub timeout and boot into a failsafe terminal.

Then:
```
sudo cp /etc/X11/xorg.conf /home/[yourhome]/
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by Ragged on 2009-04-27
Well, I entered that, but it didn't seem to work, nor did the automatic X11 fix offered, but when mashing the keys in frustration, both mouse and keyboard started working. Either the fix had a delayed reaction, or my the computer was just playing with me :-k . Thanks for the speedy response, hopefully the transition to Jaunty will occur more smoothly [-o<

---

