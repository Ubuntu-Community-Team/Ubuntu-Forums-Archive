---
title: "Can someone explain Gnu Grub"
date: 2010-07-25
forum: New to Ubuntu
---

### Post by lonewarrior556 on 2010-07-25
I have a partition of on one computer Ubuntu/vista and ubuntu/xp on the other one. I have a very similar start up screen with Gnu Grub, what I can't understand is why i have ubuntu listed twice it says 
Ubuntu, with Linux 2.632-24-generic
Ubuntu, with Linux 2.632-24-generic (recovery mode)
Ubuntu, with Linux 2.632-21-generic
Ubuntu, with Linux 2.632-21-generic (recovery mode)
 
what is the difference between 21 and 24? they both load the same as far as i can tell. 
Can anyone explain if there's a difference and if not, why does gnu grub do that.

---

### Post by sikander3786 on 2010-07-25
Hi.

2.632-XX-Generic mentions the kernel version. Everytime you get a new kernel by updates, you get it listed and added at the Grub menu as well. You have the choice to boot the kernel you want. Nothing problematic.

Regards.

---

### Post by cavalier911 on 2010-07-25
For backup in case the updated kernel doesn't boot. After your sure the new kernel's ok, go into synaptic and remove the previous kernel,when grub updates it will remove the entry.

---

### Post by SaaTeeVaaGreen on 2010-07-25
there isnt much difference between the two. 2.6.32-24 is the latest version of the linux kernel, while 2.6.32-21 is an earlier version of it. grub will always present you with an option for each kernel that it finds on your machine. you can limit the number of kernels you are shown at boot if you want.

---

### Post by lonewarrior556 on 2010-07-26
> **SaaTeeVaaGreen said:**
> there isnt much difference between the two. 2.6.32-24 is the latest version of the linux kernel, while 2.6.32-21 is an earlier version of it. grub will always present you with an option for each kernel that it finds on your machine. you can limit the number of kernels you are shown at boot if you want.
 
Can you explain how to do that? shoudl I always load the latest kernal?

---

### Post by acreech on 2010-07-26
go to System>Administration>Synaptic Package Manager

At the top of the window where it says "Quick Search" copy and paste this into the window

```

linux-headers-2.6.32-21-generic

```

As cavalier911 suggests, it is a good idea to keep an older kernel around just incase you end up with your current kernel, you can boot into an older one and then fix any problems that you may be having. 

acreech

---

