---
title: "HP Mini 210 CPU"
date: 2010-09-12
forum: New to Ubuntu
---

### Post by ryandavis33 on 2010-09-12
I have an HP Mini 210 with a N450 Intel Atom

According to Ubuntu i have 2 cores. Under system moniter it shows the 2 cores and they operate independent. 1 would be 6% and the other and 2 would be at 60%.

In the Freq scaling applet i can alter each core as i please.

Intel, Wikipedia, and a bunch of others say the N450 has 1 core.

Whats up with this?:popcorn:

---

### Post by Silent Warrior on 2010-09-12
Hm... I don't suppose the N450 has Hyper-Threading?

---

### Post by ryandavis33 on 2010-09-12
Yes it does.

What does that mean?:popcorn::p

---

### Post by Silent Warrior on 2010-09-13
Ah, that would be the reason, then. HT kind of tricks the system into believing there are actually two cores, or maybe we should call them 'processing units'. So: Processing is done in threads, as far as I can understand. One core deals with one thread. If this core has HT, it can process an extra thread parallel to the other one. AMD (who doesn't have HT anywhere) insists this limits performance in both threads, as opposed to having one thread per actual core. But that's all academic stuff.

Summary: You see two cores in System Monitor because you have HT.

---

### Post by KristinaK on 2010-09-23
thanks, so it is normal and intended behavior? :popcorn:

---

### Post by mcduck on 2010-09-23
> **KristinaK said:**
> thanks, so it is normal and intended behavior? :popcorn:

It's intended behavior. In some situations it might improve the performance slightly (which is the reason hyperthreading exists in the first place).

..although unlike what SilentWarrior said, hyperthreading doesn't actually run two threads parallel, that would require actually having two processor cores. It executes one thread at a time, but when that one thread stops to wait for something, like getting data from RAM or your hard drive, the CPU switches to running the other thread. So it's not as good as having two actual cores, but slightly better than a single.-core CPU with no hyperthreading.

AMD doesn't use it because it's patented by Intel, they try to give you more actual cores instead. Also there has been some security issues with hyperthreading (at some point it even was disabled by default in Ubuntu), but since it's working again I suppose those security issues have been solved by now.

---

