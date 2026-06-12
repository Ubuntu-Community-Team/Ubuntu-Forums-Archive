---
title: "ubuntu 10.04 freezing"
date: 2010-07-29
forum: New to Ubuntu
---

### Post by badtazz72 on 2010-07-29
the only problem i have is i try to run vmware or vbox my computer  freeze up totally. im running Ubuntu 10.04

---

### Post by jerenept on 2010-07-29
try to limit the VM to one core. this can be set in the VM's Settings.

There will always be some performance penalty, because running a VM uses a lot of CPU.

---

### Post by badtazz72 on 2010-07-29
ok i will brb

---

### Post by badtazz72 on 2010-07-29
it was set on one cpu and ram turnd down to bare min and it still locks up

---

### Post by jerenept on 2010-07-29
did you restart after installing VBOX? What is freezing, the VM or Ubuntu itself (the host)

---

### Post by badtazz72 on 2010-07-29
ubuntu it self

---

### Post by QIII on 2010-07-29
> **jerenept said:**
> try to limit the VM to one core. this can be set in the VM's Settings.

There will always be some performance penalty, because running a VM uses a lot of CPU.

Since he only has two cores, VirtualBox will not let him assign more than one to the VM.

Whether or not a VM uses a lot of CPU depends on what you mean by that.   One assigned to the guest will not be available to the host.  However,  if both OSes are idling, both cores will be (with some overhead on the  host's core -- it is running VBox.)


BadTazz -- What else do you have running at the time?

What is your resource usage before you start VBox and turn the VM on?

---

### Post by badtazz72 on 2010-07-29
> **QIII said:**
> Since he only has two cores, VirtualBox will not let him assign more than one to the VM.

Whether or not a VM uses a lot of CPU depends on what you mean by that.   One assigned to the guest will not be available to the host.  However,  if both OSes are idling, both cores will be (with some overhead on the  host's core -- it is running VBox.)


BadTazz -- What else do you have running at the time?

What is your resource usage before you start VBox and turn the VM on?



i just installed ubuntu 9.10 64bit doing same thing

---

### Post by badtazz72 on 2010-07-29
i really dont under stand it all worked in windows also board is nvidia 680i
ram is nvidia sli 4gb ddr2 .

---

### Post by QIII on 2010-07-30
I often have two VMs running at the same time without difficulty.

Are you using the OSE version from the repos or the PEUL version from virtualbox.org?

Do you have your virtual disks (.vdi) on different physical drives than Ubuntu?  I always install VMs so that the virtual disks are on separate physical drives so I don't get read/write conflicts between the two OSes and they operate on different I/O channels.

Does Ubuntu "crash", or does the screen gray out?

---

### Post by badtazz72 on 2010-07-30
> **QIII said:**
> I often have two VMs running at the same time without difficulty.

Are you using the OSE version from the repos or the PEUL version from virtualbox.org?

Do you have your virtual disks (.vdi) on different physical drives than Ubuntu?  I always install VMs so that the virtual disks are on separate physical drives so I don't get read/write conflicts between the two OSes and they operate on different I/O channels.

Does Ubuntu "crash", or does the screen gray out?





ubuntu  locks up no gray  mouse dont move keyboard don't work and no activity from hard drive. led stops blinking its like its  been paused and the only fix is to hold power button and restart

---

### Post by QIII on 2010-07-30
Have you tried re-installing VirtualBox?  You can do that without damage to your .vdi.  After re-installation, you can just create a new virtual machine and point it at that .vdi.

Failing that, we can try something else.

If you have multiple physical drives, you could create a new virtual  machine with the virtual drive on a different physical drive than  Ubuntu.  Even a home network would work for this experiment.

I think it would be good to eliminate read/write conflicts as a cause.

This is frustrating, I know.  But it is also an intriguing technical  problem that might be very useful to others if we could solve it.

I have been virtualizing for years, and competing r/w is the only time I  have encountered anything remotely like this.  That's why I use  separate physical disks now.  But even then, I used to get the "gray  out" that would eventually resolve as the r/w issues were sorted out by  the OSes.

If I get a chance this weekend (that is, if the foster kids give me a break!) I'll see if I can do some research on what you have given for the specs on your machine and see if I can find any clues about possible problems with your hardware/BIOS that might be a problem.  I doubt that would be the problem, but you never know.

---

### Post by badtazz72 on 2010-08-19
> **QIII said:**
> Have you tried re-installing VirtualBox?  You can do that without damage to your .vdi.  After re-installation, you can just create a new virtual machine and point it at that .vdi.

Failing that, we can try something else.

If you have multiple physical drives, you could create a new virtual  machine with the virtual drive on a different physical drive than  Ubuntu.  Even a home network would work for this experiment.

I think it would be good to eliminate read/write conflicts as a cause.

This is frustrating, I know.  But it is also an intriguing technical  problem that might be very useful to others if we could solve it.

I have been virtualizing for years, and competing r/w is the only time I  have encountered anything remotely like this.  That's why I use  separate physical disks now.  But even then, I used to get the "gray  out" that would eventually resolve as the r/w issues were sorted out by  the OSes.

If I get a chance this weekend (that is, if the foster kids give me a break!) I'll see if I can do some research on what you have given for the specs on your machine and see if I can find any clues about possible problems with your hardware/BIOS that might be a problem.  I doubt that would be the problem, but you never know.




well i reinstalled it i have vmware and virtual box both do it .tryed it on back up hard drive and it still locks up . i can put windows on this pc and do  the same thing and no lock ups

---

### Post by badtazz72 on 2010-08-19
i dont wana go back to windows but this is driving me crazy

---

