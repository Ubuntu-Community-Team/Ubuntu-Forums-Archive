---
title: "Intel HD Graphics 3000 processor PLZ help now"
date: 2011-08-01
forum: New to Ubuntu
---

### Post by Objectivity on 2011-08-01
Still waiting to get an answer ...

 Is there any driver for new HD 3000 second generation driver ?   Ubuntu does not detect it automatically. Additional driver does not detect anything. I updated everything ... but still  no detection.   (( I got a headache looking at my screen searching for solution ))
  
 Here is the detail of my card ...

 *-display UNCLAIMED     
       description: VGA compatible controller
       product: 2nd Generation Core Processor Family Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list
       configuration: latency=0
       resources: memory:a0000000-a03fffff memory:90000000-9fffffff ioport:2000(size=64)
ubuntu@localhost:~$

---

### Post by lordievader on 2011-08-01
[http://intellinuxgraphics.org/documentation.html](http://intellinuxgraphics.org/documentation.html)

It says on that page that your card, the HD 3000, is supported, so give it a try.

---

### Post by Objectivity on 2011-08-01
> **lordievader said:**
> [http://intellinuxgraphics.org/documentation.html](http://intellinuxgraphics.org/documentation.html)

It says on that page that your card, the HD 3000, is supported, so give it a try.


 I DID came across that page before ...  but I do not know how to compile it ! 


 On that page it say,  get precompiled 			packages from one of the many Linux distributions.

 so, where can I get that as I have no idea how to compile it .

---

### Post by lordievader on 2011-08-01
If there are precompiled packages for this driver than there is no need to compile it. Did you check in Synaptics? (System -> Administration -> Synaptic Package Manager)

---

### Post by Objectivity on 2011-08-01
> **lordievader said:**
> If there are precompiled packages for this driver than there is no need to compile it. Did you check in Synaptics? (System -> Administration -> Synaptic Package Manager)


 I did not check that.  what should I type in search area ? Thank you though . Just intel HD 3000 ?

 I typed Intel ... just see this ...

This package provides the driver for the Intel i8xx and i9xx family
of chipsets, including i810, i815, i830, i845, i855, i865, i915, i945
and i965 series chips.

---

### Post by lordievader on 2011-08-01
Euhh good question... I guess looking for Intel might get you in the right direction. I myself have an older Intel GPU, and got intel-gpu-tools installed, but that doesn't seem like a driver. Than again I didn't need a driver with my card, it just worked out of the box.
Hopefully another member has a solution.

---

### Post by Objectivity on 2011-08-02
I found this ...  might help me and others who wants to instal linux on new HD intel graphic cards ...

 [http://www.ruinelli.ch/sandy-bridge-cpu-and-the-hd3000-gpu-in-linux](http://www.ruinelli.ch/sandy-bridge-cpu-and-the-hd3000-gpu-in-linux)

---

