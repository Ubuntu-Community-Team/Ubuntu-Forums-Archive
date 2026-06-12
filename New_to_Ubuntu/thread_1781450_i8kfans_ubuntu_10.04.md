---
title: "i8k\fans ubuntu 10.04"
date: 2011-06-13
forum: New to Ubuntu
---

### Post by Harold Bolzonya on 2011-06-13
Hello ubuntu forums first time poster, and I just want you to know I have found the support level for ubuntu via the forums tops listed support on most commercial websites and that's awesome!!!

I have solved most every issue I have had except one.  I cannot for the life of me get fan control up and running on my laptop. It overheats quickly on a half load on the CPU. Most info I found on this subject was outdated and what I did find did not work.

Here's the rundown:

ubuntu 10.04 LTS basic install via disc 10.04-02 desktop i686

Laptop:

Model: Dell Inspiron 1501
MoBo: Dell UW953
Chipset: ATI RS485M
Proc:AMD Athlon 64 TK-53
RAM:2g DDR2-800

Things I have tried:

1.installing i8kutils, i8kgkrellm and gkrellm. Running gkrellm w\ addon. Results in gkrellm listing fans as -22 no matre automatic or manual
2.running above after command: sudo modprobe force=1 the same as above.
3.running i8kfan 1 1 or i8kctl fan 2 2 or sudo variations of the above. results in report back of -1 -1 for all commands. running i8kctl results in something like: -1 'System TAG' -1 -1 -1 -1 -1
4.Trying above after running the config script for lm-sensors: sudo sensors-detect.
Results in same as above.
5.downloading and running dellfand.deb

I have all of these things currently installed so it could be some sort of process compatibility issue?

Anybody have this laptop with the same OS who got the fans running? All of these fixes were pulled from forum pages that were OLD. Any suggestions would be greatly appreciated as this one is starting to really tear at me.

Harry

---

