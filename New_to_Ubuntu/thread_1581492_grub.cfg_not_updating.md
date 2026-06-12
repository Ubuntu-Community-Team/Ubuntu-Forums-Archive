---
title: "grub.cfg not updating"
date: 2010-09-25
forum: New to Ubuntu
---

### Post by seattle vic on 2010-09-25
I've been running 10.04 and have previously noted that a kernel update did not make it to grub.cfg.  I just updated to 10.10 and the same thing happened, or rather didn't happen.

Any ideas?

---

### Post by Rubi1200 on 2010-09-25
Does running ```
sudo update-grub
``` change anything?

---

### Post by seattle vic on 2010-09-25
> **Rubi1200 said:**
> Does running ```
sudo update-grub
``` change anything?

Yes, it said that it found the latest kernel versions and updated menu.lst, although I didn't even think I had that file anymore; just grub.cfg.  Here's the result of running it:


vic@laptop:/boot/grub$ sudo update-grub
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.35-22-generic
Found kernel: /boot/vmlinuz-2.6.32-24-generic
Found kernel: /boot/vmlinuz-2.6.32-23-generic
Found kernel: /boot/vmlinuz-2.6.32-22-generic
Found kernel: /boot/vmlinuz-2.6.32-21-generic
Found kernel: /boot/vmlinuz-2.6.32-20-generic
Found kernel: /boot/vmlinuz-2.6.32-19-generic
Found kernel: /boot/vmlinuz-2.6.32-18-generic
Found kernel: /boot/vmlinuz-2.6.32-17-generic
Found kernel: /boot/vmlinuz-2.6.31-20-generic
Found GRUB 2: /boot/grub/core.img
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

What I had been using to update the grub.cfg is: sudo grub-mkconfig -o /boot/grub/grub.cfg, and had done that several times.

I thought that the menu.lst was associated with grub and grub.cfg a product of grub2.  Very confusing.

In any event, I know how to update it manually, but running update manager when a kernel changes does not seem to make it happen automatically.

---

### Post by muteXe on 2010-09-25
Hello Mr Vic,
This:
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
is essential reading for grub2.  It's also very well-written and very clear.

Cheers,

mute

---

### Post by philinux on 2010-09-25
> **seattle vic said:**
> I've been running 10.04 and have previously noted that a kernel update did not make it to grub.cfg.  I just updated to 10.10 and the same thing happened, or rather didn't happen.

Any ideas?

Run the bootinfo script. Looks like grub legacy messing with grub2 or vice versa. Post back the results.txt file.

[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

---

### Post by muteXe on 2010-09-25
I thought 10.04 was grub2 as well?

---

### Post by skyjacker on 2010-09-25
> **muteXe said:**
> Hello Mr Vic,
This:
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
is essential reading for grub2.  It's also very well-written and very clear.

Cheers,

muteI,ve been hunting some good info on grub2... Thanks for the link,   skyjacker:P

---

