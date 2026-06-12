---
title: "removing grub2 garbage entries"
date: 2011-02-08
forum: New to Ubuntu
---

### Post by degarb on 2011-02-08
I just installed 10.1 on a machine.  The sleep didn't work, but hybernation works well.  However after several boots, it went from one linux (+safemode) entry in grub to 3!   I am wondering if these are hibernation states, or what I should do.  I click the first entry and linux boots.   Or perhaps these are added entries from grub2 updating?

It has taken something simple and cluttered it up.  Also, the 7 second boot menu time out is not working.  I must hit enter or click at grub screen to get it to boot.

---

### Post by [Snc] on 2011-02-08
> **degarb said:**
> I just installed 10.1 on a machine.  The sleep didn't work, but hybernation works well.  However after several boots, it went from one linux (+safemode) entry in grub to 3!   I am wondering if these are hibernation states, or what I should do.  I click the first entry and linux boots.   Or perhaps these are added entries from grub2 updating?

It has taken something simple and cluttered it up.  Also, the 7 second boot menu time out is not working.  I must hit enter or click at grub screen to get it to boot.

Those are entries for older versions of kernel. Every time, your OS updates a kernel, an additional Grub entry is made, so that you can still boot, if the newer kernel does not satisfy you (or even breaks something, that was working), it is advisable, to keep at least one older version.

You can remove old (not used) kernel packages in synaptic, but be very careful!
[Here]("http://tombuntu.com/index.php/2007/10/17/remove-ubuntu-kernels-you-dont-need/") is how to remove them.

---

### Post by ajgreeny on 2011-02-08
Can you post the output of ```
grep menuentry /boot/grub/grub.cfg
```which will show us everything that you see in the grub menu.  From that it may be easy to suggest a clean-up operation for you.

---

