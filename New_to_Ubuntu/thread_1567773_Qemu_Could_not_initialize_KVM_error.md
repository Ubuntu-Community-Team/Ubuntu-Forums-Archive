---
title: "Qemu: Could not initialize KVM error"
date: 2010-09-04
forum: New to Ubuntu
---

### Post by Fanatico on 2010-09-04
I am trying to run Qemu on Ubuntu 9.10:

mats@mats-desktop:~/felabs/sysdev/kernel$ qemu -m 32 -kernel linux-2.6.35.4/arch/x86/boot/bzImage -append "root=/dev/hda rw" -hda data/linux_i386.img

I am getting the following error:

open /dev/kvm: No such file or directory
Could not initialize KVM, will disable KVM support

What could be wrong?

My computer hardware doesn't support KVM, How can I force Qemu DO NOT use KVM?

Thanks in advance

---

### Post by jaksun5 on 2010-10-11
I'm a total linux noob but could that mean that the service/operation/user doesn't have access to that folder?

---

### Post by jaksun5 on 2010-10-15
I had the same problem and got around it by running as root, I'm sure this isn't what you are meant to do but in the absence of someone who knows I hope it helps

---

