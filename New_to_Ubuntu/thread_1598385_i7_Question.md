---
title: "i7 Question"
date: 2010-10-16
forum: New to Ubuntu
---

### Post by mattbutsko on 2010-10-16
I just installed Ubuntu 10.10 on my new Viao (man have the default themes come a long way).

Anyway, here's the specs.

Intel Core i7 Q740, quad core, 1.73Ghz, hyperthreaded
nVidia GTX 425M, 1GB VRAM in DDR3
4GB DDR3 RAM

It's a 32bit install because of some serious driver issues, so only 3.2 gigs of ram is seen, big deal. Now, the i7 automatically overclocks itself when it needs it, mine can max up to 2.93GHz per core, and it works well on Windows.

My question is, does that work on Ubuntu? Does anyone know if it's on the hardware level or is there a driver needed for it work?

Graphics (Conpiz Fusion) also seem a step down from my old laptop, which had a 2.0GHz Core 2 Duo and a nVidia Geforce Go 7400.

Kinda interesting.

---

### Post by MooPi on 2010-10-16
A simple test would be in terminal when the computer is idle . The results will show the CPU frequency.
```
cat /proc/cpuinfo
```
Then start a cpu intensive application like encoding music or video and run the same command and see if the system ramps up the frequency.

---

