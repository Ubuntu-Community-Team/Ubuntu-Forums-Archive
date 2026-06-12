---
title: "corrupted low memory?"
date: 2010-08-21
forum: New to Ubuntu
---

### Post by Chris1274 on 2010-08-21
So after installing the new kernel and thereby solving one problem, I've now got a new one.

When I boot up I'm greeted with this message:

```
[    60.881427] Corrupted low memory at c000659c (659c phys) = 00001a00
[    60.882418] Memory corruption dedected in low memory
```

Is this just a bug in the kernel or is it something I need to be worried about (or both)?

---

### Post by Rubi1200 on 2010-08-21
Do you still have the Ubuntu CD?

If yes, I would boot the computer with it and use Memtest to check your system.

Let it run, it can take quite some time.

If there are problems, they will be reported and you may have to replace your RAM.

Hope this helps.

---

### Post by Chris1274 on 2010-08-21
I booted from a usb, but I believe I can do the memtest from the grub menu. I hope that's not the issue though, I just got this machine from HP a few days ago.

---

### Post by Chris1274 on 2010-08-21
You were right, I had to run the memtest from the liveUSB after all. When I tried using the grub menu it would only get through part of the test and then reboot. Hmm ...

In any event, no errors were found, so it must be a kernel bug. This only started happening after I installed the new kernel.

I'm going to try a fresh install of the 64-bit platform. Right now I'm running the i386 version on a 64-bit machine. That's not supposed to be a problem, but we'll see what happens.

---

### Post by Rubi1200 on 2010-08-21
> **Chris1274 said:**
> You were right, I had to run the memtest from the liveUSB after all. When I tried using the grub menu it would only get through part of the test and then reboot. Hmm ...

In any event, no errors were found, so it must be a kernel bug. This only started happening after I installed the new kernel.

I'm going to try a fresh install of the 64-bit platform. Right now I'm running the i386 version on a 64-bit machine. That's not supposed to be a problem, but we'll see what happens.
A fresh install should hopefully fix any problems and 64-bit on 64-bit would seem to make sense.

Good luck!

:-)

---

### Post by Chris1274 on 2010-08-22
So changing to the 64-bit platform didn't solve the issue. I still get the corrupted low memory message, and only *after* I installed the 2.6.34 kernel, so it's obviously a kernel bug. Oh well, it's not affecting any functionality as far as I can tell. The only annoyance is that the message pops up when I open a tty terminal. I can live with that.

---

### Post by Rubi1200 on 2010-08-22
You might want to consider submitting a bug report on launchpad about this.

In any event, I am pleased you got things working again (sort of).

:-)

---

### Post by nutznboltz on 2010-10-11
Can you please test and report if this works?

memory_corruption_check_size=128K

in the boot options.

The default is

memory_corruption_check_size=64K

but it seems that's not enough for some systems.

Thanks

If you don't know how to set BootOptions read

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

Also this thread is very important to anyone looking at this bug

[http://linux.derkeiler.com/Mailing-Lists/Kernel/2009-07/msg04621.html](http://linux.derkeiler.com/Mailing-Lists/Kernel/2009-07/msg04621.html)

---

### Post by iandouglas on 2010-10-26
> **nutznboltz said:**
> Can you please test and report if this works?

memory_corruption_check_size=128K

I couldn't figure out where to add this option to add it to grub every time, so I added it manually. Unfortunately, even after a reboot, I still get the error. 

Dell/Alienware m17x, 8GB RAM, running latest 10.10 release (64-bit) and all available updates.

I'd love to hear a solution for this, it really slows down my system.

---

### Post by [Neurotic] on 2010-11-21
I'm also struggeling to work out where to set this option on a Grub2 system.

I had a look at the BootOptions wiki, and it seemed limited to Grub1.

For Grub2, is it just a case of:

```

menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd3,5)'
	search --no-floppy --fs-uuid --set cdde25d2-a4fa-48b6-b564-27377f1ee0ef
	linux	/boot/vmlinuz-2.6.32-25-generic root=UUID=cdde25d2-a4fa-48b6-b564-27377f1ee0ef ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-25-generic
        memory_corruption_check_size=128K
}

```

Would that be correct?

---

