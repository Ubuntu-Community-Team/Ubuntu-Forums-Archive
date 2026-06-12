---
title: "How do I set the default OS in Grub2?"
date: 2009-11-08
forum: New to Ubuntu
---

### Post by MindRiot on 2009-11-08
Look, I don't welcome the changes to Grub. If the Linux/Ubuntu community is going to opt for a more complicated implementation of Grub, then in the spirit of making Ubuntu easy to use, please provide a gnome-based application to change the settings. By the way, the Startup Manager doesn't work.

By looking in /etc/default/grub I see the entry "GRUB_TIMEOUT=10" I assume changing the value will determine how many seconds I have to make a choice.

I also see in /etc/default/grub the entry "GRUB_DEFAULT=0"  Does GRUB_DEFAULT= determine which menu entry is selected by default and, if so, how exactly, in the absence of "/boot/grub/menu.lst" do I determine the numerical value that would represent the Vista bootloader entry in the Grub boot menu?

Any assistance is appreciated.

~Mike Kilgore

---

### Post by ranch hand on 2009-11-08
You have got it.   That is the same entry as in grub-legacy but in a different place.  You do need to run "sudo update-grub" after you change the default.

You can take a look at /boot/grub/grub.cfg for the position of any entry on your menu.

---

### Post by MindRiot on 2009-11-08
Ranch Hand, it is your thread, in fact, that pointed me to the new location, so I thank you for taking the time to create that thread. Now that I know I have the correct configuration file, I still need to know how I determine the numerical value for "GRUB_DEFAULT="  In legacy GRUB, in Ubuntu 9.04, the value for the Vista bootloader was 4.  However, without /boot/grub/menu.lst I cannot see how many headers there might be. Do I need to discover the number by trial and error?

---

### Post by Paqman on 2009-11-08
Easiest thing to do by far is just install startupmanager and pick the one you want from the drop-down box.

---

### Post by ranch hand on 2009-11-08
The /boot/grub/grub.cfg file is where your menu comes from.  You can view it as root (it is a read only for root).  Remember to start counting at 0 and count all the menuentries to your MS entry and you should have it.

Making /boot/grub/grub.cfg read only for root is probably the biggest irritation for folks.  It is a good idea.   When you add another OS it, of course, thakes over boot/root and has all the OS listed.  In grub-legacy you need to go in and edit the menu.lst file and then get your LiveCD out to change boot/root.  With grub2 all you need to do is boot to the OS you want as boot/root, run update-grub, and "sudo grub-install /dev/sda" (or what ever for your box) and you have changed the boot root and gotten all the OS' on that grub.cfg.

That said, /etc/grub.d/30_os-prober needs a lot of work yet.  It does well with debian based OS' and MS but has problems with Red Hat based OS' and some other OS'.

Custom menus  are your friend in these cases.

---

### Post by ranch hand on 2009-11-08
> **Paqman said:**
> Easiest thing to do by far is just install startupmanager and pick the one you want from the drop-down box.
SUM should do this.  However it is not completely in sync with grub2, use with caution.

---

### Post by Paqman on 2009-11-08
> **ranch hand said:**
> SUM should do this.  However it is not completely in sync with grub2, use with caution.

It does seem to work fine. I notice that SUM came and went a few times during Alpha/Beta, but the versions of Grub and SUM we've got right now seem to play nicely, for this simple task at least.

---

### Post by MindRiot on 2009-11-08
Thanks Ranch Hand, I'll take a look at boot/grub/grub.cfg.


> **Paqman said:**
> Easiest thing to do by far is just install startupmanager and pick the one you want from the drop-down box.

I've already tried that and it does not work. If I use Startup Manager to change the settings, Grub loading... hangs indefinitely on restarting computer.

---

### Post by Paqman on 2009-11-08
> **MindRiot said:**
> 
I've already tried that and it does not work. If I use Startup Manager to change the settings, Grub loading... hangs indefinitely on restarting computer.

Well, then i'll eat my words and say: edit /etc/default/grub as mentioned above.

---

### Post by drs305 on 2009-11-08
Here's a link if you still don't have it figured out:
[GRUB 2 - 5 Common Tasks]("http://ubuntuforums.org/showthread.php?t=1302743")

---

### Post by MindRiot on 2009-11-08
I'm all set now. The value was the same as it was in legacy GRUB.

@Ranch Hand, Thanks for the assistance.

@Paqman, perhaps Startup Manager didn't work due to the configuration of my system. After all, I have four hard drives and two other operating systems other than Ubuntu.

@drs305, thanks for the link.

---

