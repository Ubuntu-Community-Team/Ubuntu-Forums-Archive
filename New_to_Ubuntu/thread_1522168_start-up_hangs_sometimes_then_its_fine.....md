---
title: "start-up hangs sometimes then its fine...."
date: 2010-07-01
forum: New to Ubuntu
---

### Post by listerdl on 2010-07-01
Hi, every now and again, in fact rarely, my boot into ubuntu hangs on a black screen,,,,

any idea what checks or scans i could do to see why this is?

thanks!

---

### Post by Darkness Des on 2010-07-01
If you could please post some specs about your computer, I would be much more capable to help you. For now, though, my guess is that your Video Card isn't up to par with the bootsplash. This happened on my old computer, and as soon as I put the hard drive in this computer I stopped having the problem.

---

### Post by listerdl on 2010-07-01
Hi thanks for your reply:

**Panasonic Toughbook Specs:**
[B]
MS Windows 7 Ultimate and Latest and Updated Ubuntu 32-bit[/B]
 
Intel Core 2 Duo CPU U9400 @ 1.40HGz, 2.0GB RAM, Mobile Intel 4 Series Express Chipset Family

---

### Post by k3lt01 on 2010-07-01
When it hangs is it after an update and reboot?

---

### Post by listerdl on 2010-07-02
> **k3lt01 said:**
> When it hangs is it after an update and reboot?

not necessarily but it might actually be that now that you mention it.....i mean it happens rarely so it might just be something connected to that.

What is it about an update that would cause it to hang like that?

Anyhting I can do?

Thanks!!!

---

### Post by k3lt01 on 2010-07-02
Any updates that change a file that is used at boot up will cause ureadahead to "reprofile" the boot sequence. On a low powered machine with very little RAM it can cause delays in booting. On some machines, my laptop for example, it literally cripples it unless I do a hard reboot.

I would make sure that this is the issue before I did anything, but if it is you can remove ureadahead in Synaptic. I must say that ureadahead has a purpose and I would only rmove it if it is the issue.

---

### Post by listerdl on 2010-07-02
> **k3lt01 said:**
> Any updates that change a file that is used at boot up will cause ureadahead to "reprofile" the boot sequence. On a low powered machine with very little RAM it can cause delays in booting. On some machines, my laptop for example, it literally cripples it unless I do a hard reboot.

That sounds very likely - thanks for that....

What is a hard boot? How do you do that?

---

### Post by k3lt01 on 2010-07-02
> **listerdl said:**
> That sounds very likely - thanks for that....

What is a hard boot? How do you do that?Hard reboot is when you hold the power button till it shuts down or pull the power. It is when you force the PC to shut down. It isn't good practise because it can cause corruption on the hard drive.

---

### Post by listerdl on 2010-07-05
its done it again but this time it wasnt over an update it was just over a regular switching OS's

what could be making it hang u reckon?

any checks that i can perform?

PS proabably unrelated but my swap file is non existant - could this be the issue?

---

### Post by k3lt01 on 2010-07-05
> **listerdl said:**
> PS proabably unrelated but my swap file is non existant - could this be the issue?I would think it could be but can't give a definitive answer. I have 2gb SWAP on all my machines regardless of RAM.

---

