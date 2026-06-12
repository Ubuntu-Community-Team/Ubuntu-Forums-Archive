---
title: "Dynamic Loading of Kernel Modules"
date: 2010-05-12
forum: New to Ubuntu
---

### Post by Ozymandias_117 on 2010-05-12
Hi, I was just wondering, isn't the ability to dynamically load and unload kernel modules while the operating system is running one of the benefits of Linux? Although, with this being the case, after generating proprietary kernel modules (drivers) for a graphics card, it says I must completely reboot my system. Why can't they be loaded and Xorg be restarted? Or am I completely confused about something? :D

This is pretty much a theoretical discussion so I can find out if I understand this correctly or not. :D Thanks in advance for your answers!

---

### Post by -humanaut- on 2010-05-12
Nvidia modules "taint" the kernel thats why you have to restart but you can just kill X generally to reload the kernel modules for X there are dynamic settings with KMS for example set NOMODESET will set the kernel module to not probe for video cards, sounds cards, etc... You can check [http://tldp.org](http://tldp.org) search KMS and learn the commands theres quite a large number of them.

---

### Post by Ozymandias_117 on 2010-05-12
> **-humanaut- said:**
> Nvidia modules "taint" the kernel thats why you have to restart but you can just kill X generally to reload the kernel modules for X
> there are dynamic settings with KMS for example set NOMODESET will set the kernel module to not probe for video cards, sounds cards, etc...

Just want to see if I'm understanding... At first it seems like you are saying that you CAN just restart X instead of rebooting, but then it sounds like you're saying I would have to have already set the kernel to NOMODESET before it would work....? And I'll look over there for more info too.

Edit: Also, you specifically stated Nvidia, I assume ATI's are designed the same way?

---

### Post by -humanaut- on 2010-05-13
> **Ozymandias_117 said:**
> Just want to see if I'm understanding... At first it seems like you are saying that you CAN just restart X instead of rebooting, but then it sounds like you're saying I would have to have already set the kernel to NOMODESET before it would work....? And I'll look over there for more info too.

Edit: Also, you specifically stated Nvidia, I assume ATI's are designed the same way?

Let me clarify. You can restart X for X specific modesettings NOMODESET would require a reboot but installing the Nvidia driver would require you to Kill X. I honestly don't know about ATI cards I heard they were being open-sourced but I don't know if thats true or not I haven't used an ATI card in years.

---

