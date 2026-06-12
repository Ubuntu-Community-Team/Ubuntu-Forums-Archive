---
title: "my ps2 mouse stopped working after I upgrade to Jaunty"
date: 2009-10-20
forum: New to Ubuntu
---

### Post by legolas_w on 2009-10-20
Hi
I upgraded a system to jaunty and now the ps2 mouse stopped working.

I tried:


```
sudo rmmod psmouse
```

and the result was:

```
ERROR:  module psmouse does not exist in /proc/modules
```

I checked all files in /etc/modprobe.d to see whether it is blocklisted by accident or not and none of those files contain anything similar to psmouse inside them.

Any help is really welcome

---

### Post by legolas_w on 2009-10-21
Any comment?
Thanks.

---

### Post by Mark Phelps on 2009-10-21
I found the same problems upgrading a laptop from 7.10.  I posted, went through LOTS of suggested solutions -- nothing worked.

You could try getting a PS/2-to-USB adapter for your mouse (presuming you have USB ports on your machine).  That's what worked for me.

---

### Post by shirsch on 2009-10-23
> **legolas_w said:**
> Hi
I upgraded a system to jaunty and now the ps2 mouse stopped working.


Something changed in the PS2 aux port driver with kernel 2.6.28-16 that screws up hardware detection.  Try adding 'i8042.nopnp' to the list of boot arguments. This is done by editing /boot/grub/grub.lst.

---

### Post by legolas_w on 2009-10-26
> **shirsch said:**
> Something changed in the PS2 aux port driver with kernel 2.6.28-16 that screws up hardware detection.  Try adding 'i8042.nopnp' to the list of boot arguments. This is done by editing /boot/grub/grub.lst.

Hi
There was no file with that name in that directory, I created the file and added the i8042.nopnp  into it. but it I do not have the mouse working :(


Any advise? maybe I am making mistake with adding the code into the file?


Thanks

---

### Post by SunnyRabbiera on 2009-10-26
That is quite unusual, maybe a fresh install would have been better.

---

