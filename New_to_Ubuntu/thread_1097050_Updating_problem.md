---
title: "Updating problem"
date: 2009-03-15
forum: New to Ubuntu
---

### Post by Volt9000 on 2009-03-15
I've had this little update icon in the notification area for awhile and after reading several posts which always encourage do accept all updates, I did. Well when the update process finished I was told there was an error. I opened up the details window and found this at the end:

> 
E: /var/cache/apt/archives/linux-image-2.6.27-7-generic_2.6.27-7.16_i386.deb: failed in buffer_write(fd) (11, ret=-1)
E: /var/cache/apt/archives/openoffice.org-core_1%3a2.4.1-11ubuntu2.1_i386.deb: failed in buffer_write(fd) (11, ret=-1)


So I run Synaptic package manager, which gave me an error when I tried to start it from the menus, so I had to run it from the command-line with sudo.
It tells me I have 8 broken packages as follows:
openoffice.org-calc
openoffice.org-draw
openoffice.org-gnome
openoffice.org-gtk
openoffice.org-impress
openoffice.org-math
openoffice.org-writer
python-uno


Well I decide to restart Ubuntu first and fix them after. When it restarted (booted into the new kernel 2.6.27-11), the graphical interface wouldn't load at first, then it loaded and said my nvidia settings are no good, so it will run in low-res mode with enhanced graphics disabled.

At this point I restarted the system and booted back into the previous kernel (2.6.27-7) and the resolution is now restored. I checked Synaptic and it still tells me I have 8 broken packages, same as before. I try to re-install them, fix them, nothing works-- I still get an error.

What happened to my system? :(

---

### Post by taurus on 2009-03-15
Try running these from a terminal.

```
sudo apt-get -f install
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by Volt9000 on 2009-03-15
Ok I ran the first two and now I'm running upgrade but it's gonna be a while.
In the meantime, what do these commands do?

[Edit]
Hmm it seems that this problem stems from insufficient disk space.
Well that would be the problem-- my / partition is nearly 100% full.

Dammit... when I installed Ubuntu I manually set up the partitions, and the guide I was using suggested 2-3GB for the root partition.

---

### Post by taurus on 2009-03-15
The first one is the one that does all the hard work.

```

NAME
       apt-get - APT package handling utility -- command-line interface


       -f, --fix-broken
           Fix; attempt to correct a system with broken dependencies in place.
           This option, when used with install/remove, can omit any packages
           to permit APT to deduce a likely solution. Any Package that are
           specified must completely correct the problem. The option is
           sometimes necessary when running APT for the first time; APT itself
           does not allow broken package dependencies to exist on a system. It
           is possible that a system´s dependency structure can be so corrupt
           as to require manual intervention (which usually means using
           dselect(8) or dpkg --remove to eliminate some of the offending
           packages). Use of this option together with -m may produce an error
           in some situations. Configuration Item: APT::Get::Fix-Broken.

```

---

### Post by Volt9000 on 2009-03-15
> **taurus said:**
> The first one is the one that does all the hard work.



That's funny because that command was real quick.
It's the last command that's taking a while. Downloading everything and now unpacking and replacing.

---

### Post by Volt9000 on 2009-03-15
Ok well I resized the partitions and all seems to be well now.

However now when I start in either kernel, after the preliminary loading screen, where the orange bar is going back and forth, I'll get a plain-text screen which shows all the modules loading. What happened to the regular progress bar? How can I get it back?

Furthermore, if I boot the new kernel, Ubuntu will complain it can't find the nvidia drivers in the kernel (can't remember the exact error message) and I have to start up in low-res mode. But if I boot the old kernel it works just fine. How do I fix this?

[Edit]
I should mention, after changing around the partitions I edited /etc/fstab and changed the UUIDs according to the output of blkid. I did NOT edit grub's menu.lst file (the "quiet" option is still present.)

---

### Post by Volt9000 on 2009-03-15
Ok, well I booted into 2.6.27-11 and the error message is:

HDIO_DRIVE_CMD failed: Input/output error

I only get this error when I boot into 2.6.127-11, not 2.6.27-7 (original kernel.)


Regarding the graphics: I tried installing the nvidia kernel drivers from Administration > Hardware drivers. I choose the recommended driver (version 177) from the list and click Activate, and after authenticating a dialog called "Downloading and installing driver" comes up and immediately disappears, leaving the driver unactivated.

What's going on?

---

### Post by Shazaam on 2009-03-15
> **Volt9000 said:**
> 
However now when I start in either kernel, after the preliminary loading screen, where the orange bar is going back and forth, I'll get a plain-text screen which shows all the modules loading. What happened to the regular progress bar? How can I get it back?

I had a similar problem. See if caljohnsmith's posts help you...
[http://ubuntuforums.org/showthread.php?t=1057823](http://ubuntuforums.org/showthread.php?t=1057823)

---

### Post by Volt9000 on 2009-03-15
Alright, I'll take a look.
But first and more importantly... why can't I enable nvidia drivers in the newer kernel?

---

### Post by Volt9000 on 2009-03-16
Thanks for the link Shazaam, works like a charm!

I also somehow got my nvidia drivers working. Dunno how.

---

