---
title: "A way to reboot into windows from terminal...?"
date: 2010-07-22
forum: New to Ubuntu
---

### Post by someoney3000 on 2010-07-22
Hello,

I've instaexlled ubuntu and windows in separate partitions.  I have it booted as ubuntu right now (and prefer to keep it that way).  Is there a way to reboot it to windows remotely?

I understand I can edit some grub options so that when I reboot, it automatically selects the window partition.  I'm not sure if I can reboot it back to ubuntu if I do that though.

Is there a way to remotely reboot it to windows without setting the default grub selection?

Thank you for your time.

---

### Post by bodhi.zazen on 2010-07-22
Yes, see grub-reboot

[http://manpages.ubuntu.com/manpages/lucid/en/man8/grub-reboot.8.html](http://manpages.ubuntu.com/manpages/lucid/en/man8/grub-reboot.8.html)

That command (temporarily) sets the default OS to boot , then reboot.

---

### Post by someoney3000 on 2010-07-22
> **bodhi.zazen said:**
> Yes, see grub-reboot

[http://manpages.ubuntu.com/manpages/lucid/en/man8/grub-reboot.8.html](http://manpages.ubuntu.com/manpages/lucid/en/man8/grub-reboot.8.html)

That command (temporarily) sets the default OS to boot , then reboot.

Thank you!  That was extremely simple.

---

