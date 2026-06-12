---
title: "Installing Tor and Privoxy on a flash drive"
date: 2011-08-23
forum: New to Ubuntu
---

### Post by Inodoro Pereyra on 2011-08-23
Ok, so I installed the Tor browser package on a flash drive, and I want to install Privoxy on it, so I can run them both together from the flash drive, on any computer, other than the one I'm using now.
But, so far, I haven't been able to find any instructions on how to do that. Is there some kind of a tutorial on how to install Privoxy on a flash drive?

Thanks in advance. :)

---

### Post by Inodoro Pereyra on 2011-08-24
Bump? :(

---

### Post by Inodoro Pereyra on 2011-08-25
Ok, so I assume nobody knows.

What about Polipo? Is it better or worse than Privoxy? I'm not interested in ad blocking, but only in privacy and anonymity. For what I read (correct me if I'm wrong), the main privacy issue with Tor is DNS leaks, which are solved with Privoxy. Does Polipo do the same?

Last, in the Tor pages it says Polipo is included in the Tor Browser Bundle, yet I can't find it in mine. Should I install it separately?

---

### Post by Inodoro Pereyra on 2011-09-05
Wow, almost 130 views, and not a single reply...
Nobody knows? :(

Let's see if I get lucky this way:

Does anybody know of ANY proxy I can install in a flash drive, that would solve Tor's privacy issues?:confused:

---

### Post by DZ* on 2011-09-05
I guess what's confusing in your question is an implication that an install of privoxy (or anything else for that matter) to a flash is any different than its install to a hard drive.

You can do a "regular" install of Ubuntu to a flash drive, the same way as if it was a hard drive. Just make sure you install grub on the stick as well. That way, you can install anything you want on that stick. I have a stick that survived a whole series of OS upgrades (since Hardy Heron IIRC) and it boots from all kinds of computers.

---

### Post by Inodoro Pereyra on 2011-09-05
Thank you DZ* for the reply.

The thing is, I don't really want to install Ubuntu on a stick. 
I have a 2GB stick, which is more than enough to install the Tor Browser Bundle in it. The initial idea was to install either Privoxy or Polipo in the same stick, so I could use the stick on any computer, without the need to reboot.

Either way, if, as a last resort, I have to install Ubuntu on the flash drive, what capacity FD I need?

---

### Post by vasa1 on 2011-09-05
> **DZ* said:**
> ...
You can do a "regular" install of Ubuntu to a flash drive, the same way as if it was a hard drive. **Just make sure you install grub on the stick as well.** That way, you can install anything you want on that stick. I have a stick that survived a whole series of OS upgrades (since Hardy Heron IIRC) and it boots from all kinds of computers.
Something like this?
[http://www.pendrivelinux.com/install-grub2-on-usb-from-ubuntu-linux/](http://www.pendrivelinux.com/install-grub2-on-usb-from-ubuntu-linux/)

I'd like to look at such an option. Beats messing with the hard disk :) but I'd love to get more details on how this will  work. Do we then need two sticks, one just to provide the GRUB and one to carry the OS? <<< newbie alert!

---

### Post by DZ* on 2011-09-05
> **vasa1 said:**
> Something like this?
[http://www.pendrivelinux.com/install-grub2-on-usb-from-ubuntu-linux/](http://www.pendrivelinux.com/install-grub2-on-usb-from-ubuntu-linux/)

I'd like to look at such an option. Beats messing with the hard disk :) but I'd love to get more details on how this will  work. Do we then need two sticks, one just to provide the GRUB and one to carry the OS? <<< newbie alert!

There is no difference between installing Ubuntu to the hard drive and installing it onto a USB-connected flash. I think you need a minimum 8Gb stick (yes, a single one) for a good experience. You just need to choose the correct target media during the install and watch that the grub goes to the flash drive too. A foolproof way to ensure that is to disconnect the hard drive before the installation.

---

### Post by Inodoro Pereyra on 2011-09-05
Thanks again.
But (correct me if I'm wrong), if I install Ubuntu on a flash drive, every time I try to use it on a different computer, I'd have to load the drivers for that computer...right? (I'm specifically thinking about the wifi drivers)

---

### Post by DZ* on 2011-09-05
> **Inodoro Pereyra said:**
> Thanks again.
But (correct me if I'm wrong), if I install Ubuntu on a flash drive, every time I try to use it on a different computer, I'd have to load the drivers for that computer...right? (I'm specifically thinking about the wifi drivers)

I installed a Broadcom wifi driver once, but after that a correct one is being activated depending on which computer its booted from (without my participation). I only tried wifi on computers with Intel wireless cards and a Broadcom.

Don't install proprietary video drivers if you'd like to be able to boot from different computers.

---

### Post by Inodoro Pereyra on 2011-09-05
Ok, I'll try it. Thank you. :D

---

