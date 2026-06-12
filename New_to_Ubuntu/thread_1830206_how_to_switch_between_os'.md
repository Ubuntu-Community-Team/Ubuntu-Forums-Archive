---
title: "how to switch between os' ?"
date: 2011-08-21
forum: New to Ubuntu
---

### Post by neil_1 on 2011-08-21
Is there a way to switch between os's (ubuntu - win7) without reboot ?
and then i can switch back and continue what i was doing on ubuntu without reboot ?

---

### Post by sanderd17 on 2011-08-21
You can run both simultaniously (one real and one virtual) if you want. Check out Virtualbox. But if you have a normal dual boot, this is not possible.

---

### Post by SoFl W on 2011-08-21
If you boot with one system and put the other in a virtual system then yes it is possible.  Otherwise no.

Look into Virtualbox and VMware.  I boot with Ubuntu and I use Windows inside a virtualbox machine if I need to.

---

### Post by neil_1 on 2011-08-22
I know about virtual machines, i use vmware
but just wanted to know if it was possible to run both simultaneously using dual boot :/

---

### Post by x-D on 2011-08-22
> **neil_1 said:**
> I know about virtual machines, i use vmware
but just wanted to know if it was possible to run both simultaneously using dual boot :/

That probably won't be possible, because the different OSes are sharing resources and maybe hogging some files that the other needs to use in some case.

But if it is possible, it would be really slow and laggy, due to the reasons I just stated above ^^^^^!

Hope this helps....

x-D :guitar:

---

### Post by sanderd17 on 2011-08-22
> **neil_1 said:**
> I know about virtual machines, i use vmware
but just wanted to know if it was possible to run both simultaneously using dual boot :/

Maybe if you have two processors, two hdds, two ram slots, two graphical cards, two ... (but that would make two computers running together not?)

---

### Post by anewguy on 2011-08-22
Run 2 items from the grub menu simultaneously - like ubuntu and windows???

Short answer - no.

---

### Post by elliotn on 2011-08-22
impossible

---

### Post by Mark Phelps on 2011-08-22
> **sanderd17 said:**
> Maybe if you have two processors, two hdds, two ram slots, two graphical cards, two ... (but that would make two computers running together not?)

NO -- because there is, after all, only ONE set of system memory -- and two OS's can't share that memory space.

---

### Post by sanderd17 on 2011-08-22
> **Mark Phelps said:**
> NO -- because there is, after all, only ONE set of system memory -- and two OS's can't share that memory space.

Just joking, should have added a smiley.

---

### Post by scottstensland on 2011-08-22
xen is a virtualization software layer which lives between the hardware and any OS
if U google : xen virtualization ubuntu 

xen allows multiple OS to run simultaneously on a given computer.
About 5 years ago the creator of xen gave a talk where I worked
and He purported to be close to having xen actually move executing
live OS's between boxes - to facilitate 0 downtime during maintenance and
load balancing.  This included preloading onto target hardware the entire address space
of an OS then finishing by xferring host/port/DNS of the OS onto the target box.

---

### Post by 3rdalbum on 2011-08-22
> **scottstensland said:**
> xen is a virtualization software layer which lives between the hardware and any OS
if U google : xen virtualization ubuntu 

xen allows multiple OS to run simultaneously on a given computer.
About 5 years ago the creator of xen gave a talk where I worked
and He purported to be close to having xen actually move executing
live OS's between boxes - to facilitate 0 downtime during maintenance and
load balancing.  This included preloading onto target hardware the entire address space
of an OS then finishing by xferring host/port/DNS of the OS onto the target box.

Fait accompli, isn't it? A while back I heard a big fuss over a demonstration of VMware migrating a live OS from one AMD CPU to a machine with a different AMD CPU with no downtime. It was even a different microarchitecture CPU.

Xen is probably the closest thing to what the OP wants. It's still virtualisation, but it's "guest-guest" instead of "guest-host".

---

### Post by scottstensland on 2011-08-22
a generation ago IBM's MVS OS routinely ran/runs multiple disparate live OS's simultaneously on same hardware - its fitting the masses now gain access to similar

---

### Post by akand074 on 2011-08-22
I'm confident my desktop can run two OSes simultaneously.
 

... actually I was about half way through an explanation as to why it would be a good idea to be able to do that (I don't see why it couldn't be possible to split your resources on boot) when I actually convinced myself there is actually no use for that over a VM. Point being anything that I don't need 100% of my hardware for, VM would work fine. Though, if there was a way to have one OS fully running while the other is hibernating in the mean time, and then relatively quickly boot the other and hibernate the current one, then that could be useful. As long as it can do it relatively quickly.

---

### Post by Mark Phelps on 2011-08-23
> **akand074 said:**
> I'm confident my desktop can run two OSes simultaneously.

One problem you're going to run into attempting this is memory management.  Typically, an OS gets loaded into low memory at a specific offset.  If two OS's both try to load themselves into the same memory space, that is going to cause major conflicts.

IF you have a memory manager, however, that can load the OSs into different spaces and make them think that they are BOTH loaded into low memory, then you might be able to run both at once.

---

### Post by neil_1 on 2011-08-26
Alrighty thanks :)
im goin to stick with vmware then :)

---

