---
title: "System Information - Where can I find it"
date: 2010-05-22
forum: New to Ubuntu
---

### Post by JaJaBinks on 2010-05-22
I am trying to locate information (spec&#347;) on my system (CPU and Graphics card in particular). I can only find info on cpu from **System/Administration/System Moniter**, so am assuming other information is only available from terminal, but no idea where to look. Any help appreciated

---

### Post by SlidingHorn on 2010-05-22
A great tool for this is sysinfo.  You can install it from the repos by going into your terminal and:

```
sudo apt-get install sysinfo
```

then when it's finished installing:

```
sysinfo
```

---

### Post by wojox on 2010-05-22
```
sudo lshw -html > ~/hardware.html
```

This will create a file in your home folder with the information.

---

### Post by JaJaBinks on 2010-05-22
> **SlidingHorn said:**
> A great tool for this is sysinfo.  You can install it from the repos by going into your terminal and:

```
sudo apt-get install sysinfo
```

then when it's finished installing:

```
sysinfo
```
Many thanks Slidinghorn. That was easy.

---

### Post by dgaud on 2010-05-22
I've been playing with this command recently and found it very useful:
[B]
sudo lshw -C display (for video info)[/B]

or 

**sudo lshw -C cpu (for cpu info)**

However, when I run it my system, I get 2 displays (!?)
```
  *-display:0             
       description: VGA compatible controller
       product: R580 [Radeon X1900 XT] (Primary)
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi bus_master cap_list rom
       configuration: driver=radeon latency=0
       resources: irq:27 memory:c0000000-cfffffff(prefetchable) memory:dfde0000-dfdeffff ioport:dc00(size=256) memory:dfe00000-dfe1ffff(prefetchable)
  *-display:1 UNCLAIMED
       description: Display controller
       product: R580 [Radeon X1900 XT] (Secondary)
       vendor: ATI Technologies Inc
       physical id: 0.1
       bus info: pci@0000:01:00.1
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:dfdf0000-dfdfffff
```

I'm just curious why?

---

### Post by JaJaBinks on 2010-05-22
Wonderful. Thanks Wojox

---

