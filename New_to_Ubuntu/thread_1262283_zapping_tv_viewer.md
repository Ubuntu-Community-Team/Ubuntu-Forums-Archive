---
title: "zapping tv viewer"
date: 2009-09-09
forum: New to Ubuntu
---

### Post by 289531.EXE on 2009-09-09
just downloaded the zapping tv viewer and keep getting this message:

couldnt open /dev/video0 tryother devices?


...something like that. can anyone help me out?

---

### Post by cariboo on 2009-09-10
Is your tv tuner card detected and the proper driver loaded? Open an Applications-->Accessories-->Terminal and type:

```
sudo lshw -C multimedia
```

and paste the output in your next post.

---

### Post by 289531.EXE on 2009-09-11
*-multimedia            
       description: Multimedia audio controller
       product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller
       vendor: Intel Corporation
       physical id: 1e.2
       bus info: pci@0000:00:1e.2
       version: 04
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=Intel ICH latency=0 module=snd_intel8x0

---

