---
title: "GRUB Error 26"
date: 2009-09-09
forum: New to Ubuntu
---

### Post by VoodooLoveDog on 2009-09-09
Having a problem with GRUB and need someone to point me in the right direction.

I'm running Ubuntu 9.04 on a Dell Studio 1555. I rebooted the other day and received this error:

Loading Stage 1.5..
Error 26

Looking at the GRUB manual it says that this means there are "Too Many Symbolic Links". Awesome, yet I see no where steps to repair GRUB or fix this problem. Any pointers?

---

### Post by LewRockwell on 2009-09-09
[http://www.linuxquestions.org/questions/linux-software-2/grub-error-26-disk-read-error-using-grub4dos-and-ubuntu-498654/?](http://www.linuxquestions.org/questions/linux-software-2/grub-error-26-disk-read-error-using-grub4dos-and-ubuntu-498654/?)

.

---

### Post by VoodooLoveDog on 2009-09-09
I fixed the problem. I booted into the Ubuntu LiveCD and ran:

```
fsck -n /dev/sda1

```
It came across a ton of errors. So then I ran:

```
fsck -y /dev/sda1 
```

This fixed all my errors and the computer rebooted without a problem.

Now I just need to figure out Bluetooth on this machine. It's driving me crazy.

Note: For others reading this, I ran the above with root privileges.

---

